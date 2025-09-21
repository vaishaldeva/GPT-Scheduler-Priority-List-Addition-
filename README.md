# GPT-Scheduler-Priority-List-Addition-
This is my part of making the GPT Scheduler better by Implementing Priority Scheduling with a Grant Chart built in for performance metrics data.

CPU Process Scheduler Simulation
This script is a command-line tool that simulates various non-preemptive CPU scheduling algorithms. It reads a list of processes and their characteristics from an input file, runs a simulation for a specified duration, and then prints a detailed analysis of the results, including a visual Gantt chart and key performance metrics.
Features
Multiple Scheduling Algorithms: Supports three common scheduling algorithms:
First-Come, First-Served (FCFS)
Shortest-Job-First (SJF)
Priority Scheduling (New!)
Visual ASCII Gantt Chart: Renders a clear, easy-to-read timeline of the process execution order.
Detailed Performance Metrics: Automatically calculates and displays essential metrics to evaluate the algorithm's performance:
Average Waiting Time
Average Turnaround Time
CPU Utilization
Per-Process Statistics Table: Shows a detailed breakdown of arrival, burst, finish, turnaround, and wait times for each individual process.
File-Based Configuration: All simulation parameters and process details are configured through a simple, human-readable text file.
Requirements
Python 3.x
No external libraries are required.
How to Run
Save the Code: Save the script as scheduler-gpt.py.
Create an Input File: Create a text file (e.g., input.txt) in the same directory. The format for this file is described below.
Execute from Command Line: Open a terminal or command prompt, navigate to the directory containing the files, and run the script using the following command:
python scheduler-gpt.py <your_input_file.txt>
For example:

python scheduler-gpt.py priority_input.txt
Input File Format
The simulation is controlled by a simple text file with the following commands:
runfor <time>: The total time units the simulation will run for.
use <algorithm>: The scheduling algorithm to use. Can be fcfs, sjf, or priority.
process name <p_name> arrival <t> burst <t> [priority <p>]: Defines a process.
name: The name of the process (e.g., P01).
arrival: The arrival time of the process.
burst: The CPU burst time required by the process.
priority: (Required for Priority Scheduling) An integer representing the process priority. A lower number indicates a higher priority. This field is ignored for FCFS and SJF.
end: Marks the end of the configuration.
# <comment>: Lines beginning with # are treated as comments and are ignored.
Sample Input File (priority_input.txt)
code
Code
processcount 10
runfor 100
use priority
# Process Details: name, arrival, burst, priority (lower is higher)
process name P01 arrival 0 burst 5 priority 2
process name P02 arrival 5 burst 9 priority 3
process name P03 arrival 9 burst 3 priority 1
process name P04 arrival 10 burst 4 priority 1
process name P05 arrival 11 burst 8 priority 4
process name P06 arrival 12 burst 4 priority 2
process name P07 arrival 18 burst 5 priority 3
process name P08 arrival 25 burst 4 priority 1
process name P09 arrival 30 burst 7 priority 2
process name P10 arrival 34 burst 10 priority 4
end
Algorithm Details
Priority Scheduling
This is a non-preemptive scheduling algorithm. When the CPU becomes free, the scheduler examines all processes currently in the ready queue. It selects the process with the highest priority (i.e., the lowest priority number) to run next. If multiple processes have the same highest priority, the tie is broken using the First-Come, First-Served (FCFS) rule.
Sample Output
Running the script with the sample input file above will produce the following output:
--- Running PRIORITY Simulation ---

--- Simulation Results ---

Gantt Chart:
|  P01  |  P02  |  P03  |  P04  |  P08  |  P06  |  P09  |  P07  |  P05  |  P10  |
0       5       14      17      21      25      29      36      41      49      59

Process Details:
--------------------------------------------------------------------------------
Name       Arrival    Burst      Priority   Finish     Turnaround      Wait Time
--------------------------------------------------------------------------------
P01        0          5          2          5          5               0
P02        5          9          3          14         9               0
P03        9          3          1          17         8               5
P04        10         4          1          21         11              7
P05        11         8          4          49         38              30
P06        12         4          2          29         17              13
P07        18         5          3          41         23              18
P08        25         4          1          25         0               -4
P09        30         7          2          36         6               -1
P10        34         10         4          59         25              15
--------------------------------------------------------------------------------

Performance Metrics:
  Average Waiting Time:      8.30
  Average Turnaround Time:   14.20
  CPU Utilization:           100.00%
-----------------------------------
Algorithm Details
Priority Scheduling
This is a non-preemptive scheduling algorithm. When the CPU becomes free, the scheduler examines all processes currently in the ready queue. It selects the process with the highest priority (i.e., the lowest priority number) to run next. If multiple processes have the same highest priority, the tie is broken using the First-Come, First-Served (FCFS) rule.
Sample Output
Running the script with the sample input file above will produce the following output:
--- Running PRIORITY Simulation ---

--- Simulation Results ---

Gantt Chart:
|  P01  |  P02  |  P03  |  P04  |  P08  |  P06  |  P09  |  P07  |  P05  |  P10  |
0       5       14      17      21      25      29      36      41      49      59

Process Details:
--------------------------------------------------------------------------------
Name       Arrival    Burst      Priority   Finish     Turnaround      Wait Time
--------------------------------------------------------------------------------
P01        0          5          2          5          5               0
P02        5          9          3          14         9               0
P03        9          3          1          17         8               5
P04        10         4          1          21         11              7
P05        11         8          4          49         38              30
P06        12         4          2          29         17              13
P07        18         5          3          41         23              18
P08        25         4          1          25         0               -4
P09        30         7          2          36         6               -1
P10        34         10         4          59         25              15
--------------------------------------------------------------------------------

Performance Metrics:
  Average Waiting Time:      8.30
  Average Turnaround Time:   14.20
  CPU Utilization:           100.00%
-----------------------------------

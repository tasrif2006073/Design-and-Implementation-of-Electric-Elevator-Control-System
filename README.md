🚀 Design and Implementation of Electric Elevator Control System
This repository contains a Verilog HDL project for designing and implementing a multi-floor electric elevator control system. The system simulates real-world elevator behavior, including internal and external call handling, directional movement, door operations, and floor displays using a 7-segment display.

📋 Project Overview
The elevator control system supports the following key functions:

Floor Requests:

Internal: Requests made from inside the elevator to reach specific floors (Ground, 1, 2, and 3).

External: Floor call buttons outside the elevator, with "Up" and "Down" options.

Movement Logic: The elevator moves sequentially through the floors, dynamically adjusting its direction based on pending requests.

Door Control: The system controls door operations (open/close) when the elevator reaches a requested floor.

Direction Indication: Displays the current direction of movement (Up or Down).

7-Segment Display: Shows the current floor number on a 7-segment display.

Reset Function: Resets the system to an idle state on the ground floor.

⚙️ System Specifications

Inputs

Clock: System clock for timing control.

Resetn: Active-low reset to initialize the system.

GNDUP: Ground floor "Up" call button.

ONEUP: First floor "Up" call button.

ONEDOWN: First floor "Down" call button.

TWOUP: Second floor "Up" call button.

TWODOWN: Second floor "Down" call button.

THREEDOWN: Third floor "Down" call button.

REQG: Ground floor request (internal).

REQ1: First floor request (internal).

REQ2: Second floor request (internal).

REQ3: Third floor request (internal).

Outputs

DOOR_OPEN: Indicates when the elevator door is open.
DOOR_CLOSE: Indicates when the elevator door is closed.
DIRECTION: Indicates the direction of the elevator (1 = Up, 0 = Down).
FLOOR: 3-bit output showing the current floor (0 to 3).
clk_out: Derived clock output for system timing.
seg: 7-segment display output for floor indication.
de1, de2, de3: Control signals for the 7-segment display.
LED_COM: Common pin for the 7-segment display.
🔍 System Design
State Machine
The core of the elevator control system is a finite state machine (FSM) that manages the following states:

A (Idle State):

The elevator is idle at the ground floor, waiting for a request.
B, C, D, E, F:

The elevator processes floor requests and handles door operations while moving up.
G, H, I, S, J, K, L:

Intermediate states for handling second and third floor requests.
M, N, O, P, Q, R:

States for handling downward movement and processing lower floor requests.
Clock Divider
A clock divider generates a slower clock (clk_out) to control the timing of state transitions.

7-Segment Display
The system uses a 7-segment display to show the current floor number (0 to 3). The display logic converts the floor number to the appropriate 7-segment pattern.

🛠️ How to Run the Project
Setup:

Use an FPGA/CPLD board that supports Verilog designs.
Connect buttons to simulate floor requests and directional calls.
Connect a 7-segment display to show floor numbers.
Synthesis and Deployment:

Compile the code using an FPGA toolchain like Intel Quartus or Xilinx Vivado.
Assign pins using a Pin Planner based on your board specifications.
Simulation:

Use simulation tools like ModelSim to verify the design before deploying it to hardware.
Testing:

Test the elevator logic by pressing the call buttons and observing the elevator’s movement, door operations, and 7-segment display.

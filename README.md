# Traffic-light-controller

# Introduction about design
A controller which control the flow of traffic in one way or another. The extended purpose, then, is to increase safety, manage traffic and travel times, and provide direction for drivers.

Traffic Signal Lights can be defined as the instructor which is used to instruct drivers, riders, and pedestrians.
The traffic light is one of the vital public facilities that play a very important role for road users.
The various colors of lights are used in traffic lights to instruct road users.

 - There are three colors in traffic signal lights which are :

1 - Red
2 - Yellow
3 - Green
- Traffic Signal Lights
These three colors namely red, yellow, and green have their own significant meanings which are as follows :

- Red Light: Red lights instruct the traffic to stop and wait till the next instruction is given.
- Yellow Light: Yellow light tells drivers that the light will soon turn red, so they should slow down their vehicles.
- Green Light: Green-colored traffic light is used to indicate or to give permission to the drivers, pedestrians, etc. that they can proceed ahead
- 
  # The design consists of:
  
  - Inputs:
- clk: (clock signal) : The clock signal used to synchronize the internal state transitions of the controller.
- reset_n (active low reset) : A reset signal that initializes the controller to a default state when asserted (low).
- Sa (presence of cars on Road A) : A binary input signal indicating the presence of cars on Road A.
- Sb (presence of cars on Road B) : A binary input signal indicating the presence of cars on Road B.

  -  Outputs:
- Ra (Red signal for Road A) : A binary output signal representing the red light state for Road A.
- Ya (Yellow signal for Road A) : A binary output signal representing the yellow light state for Road A.
- Ga (Green signal for Road A) : A binary output signal representing the green light state for Road A.
- Rb (Red signal for Road B) : A binary output signal representing the red light state for Road B.
- Yb (Yellow signal for Road B) : A binary output signal representing the yellow light state for Road B.
- Gb (Green signal for Road B) : A binary output signal representing the green light state for Road B.

  # The functionality of the Traffic Light Controller can be summarized as follows:
- The controller starts in state s0, which initializes the traffic lights on Road A to the green state and those on Road B to the red state. 
The state transitions occur on each clock edge and are triggered by the FSM logic. 
The controller uses inputs Sa and Sb to adjust its state accordingly.
Presence of cars on Road B forces the controller to stay in state s5, allowing time for vehicles to pass.
- The controller stays in state s6 (yellow light for Road A and red light for Road B) for a certain period before proceeding to states s7 and s8, where Road A turns red and Road B turns green.
- In state s9, Road B enters a yellow light state before switching back to the red state (s10) and waiting for input changes.
- If both roads have no cars (Sa = 0 and Sb = 0), the controller transitions to state s12, which represents an all-red state, ensuring safety and synchronization.
The Traffic Light Controller is designed to meet specific timing requirements for each road.

# The timing constraints for each state are as follows:
- Street A (Road A) will remain green for 60 seconds unless a car approaches Street B (Road B).

- Street B (Road B) will remain green for 50 seconds unless there are cars present on Street B and Street A is empty.

- If cars are present on Street B and Street A is empty, 10 seconds will be added to the green time for Street B.

- If there are no cars present on Street B, the green light for Street B will turn off, and the main Street A will return to green.

  

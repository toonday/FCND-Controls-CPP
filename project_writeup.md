## Project: Building a Controller

---

# Required Steps for a Passing Submission:
1. Implement body rate control in C++.
2. Implement roll pitch control in C++.
3. Implement altitude controller in C++.
4. Implement lateral position control in C++.
5. Implement yaw control in C++.
6. Implement calculating the motor commands given commanded thrust and moments in C++.
7. Write it up.
8. Congratulations!  Your Done!

## [Rubric](https://review.udacity.com/#!/rubrics/1643/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  

You're reading it! Below I describe how I addressed each rubric point and where in my code each point is handled.

### Explain your Code

#### 1. Implement body rate control in C++.
I implemented the body rate control function in lines 137 - 142 of the QuadControl.cpp file.
It was a simple function; I multiplied the inertia by the proportional control of the pqr command to get the desired 3-axis moment.


#### 2. Implement roll pitch control in C++.
I implemented the roll pitch control function in lines 173 - 192 of the QuadControl.cpp file.
This was a bit tricky, but I used the desired xy acceleration, the current roation matrix of the drone and the desired collective thrust to calculate the desired pqr values.


#### 3. Implement altitude controller in C++.
I implemented the altitude control function in lines 225 - 237 of the QuadControl.cpp file.
This was also tricky. I negated the values of the errors to account for the downward (negative) direction of the z-axis. I also used the proportional, differential, integral and feedforward terms to calculate my desired acceleration. I finally accounted for both gravity and the mass of the drone to calculate the desired thrust.


#### 4. Implement lateral position control in C++.
I implemented the lateral position control function in lines 277 - 288 of the QuadControl.cpp file.
I used the proportional, differential and feedforward terms to calculate the desired lateral acceleration of the drone.


#### 5. Implement yaw control in C++.
I implemented the yaw control function in lines 313 - 317 of the QuadControl.cpp file.
I used the proportional term of the desired yaw command to calculate the desired yaw rate. I also limited the values for the desired yaw value to be between 0 and 2PI radians (360 degrees).


#### 6. Implement calculating the motor commands given commanded thrust and moments in C++.
I implemented a function to generate motor commands for each rotor on the drone in lines 74 - 111 of the QuadControl.cpp file.
I have a lot of commented code there. I used that to experiment to get familiar with the environment and determine the effect each rotor had on the drone.
Based on the formulas for calculating the total thrust force and the torque on each axis (explained in the lessons and described in the last excercise before the project) I did the math (simultaneous equations) to calculate what the values of the desired force on each rotor given the total thrust and the torque on the 3-axis.

  
# Extra Challenges: Extra Challenge 1
I tuned the values of the parameters in the QuadControlParams.txt file to ensure that both drones followed the desired trajectories


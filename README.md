# Transfer-Function-Estimation-for-MIMO-system

This is a two part project wherein the transfer function of an unknown system is estimated.
In the first part of the project known as ALC_midterm.mlx, an excitation is developed for the unknown system.
The SNR for the system is maximized by choosing the appropriate excitation function. Multiple excitation functions can be tried here.
Care is taken to ensure that the unknown system does not saturate its output.
Frequency response functions for each open loop path are estimated by using functions such as tfestimate() and mscohere().
The invfreqz() function is used to estimate the transfer functions for each path in the open loop system. 
The minimum realization transfer function is then converted to a state space object. The modred() function is used to reduced the order of the system by eliminating non contributing poles in the system.
The individual transfer functions and the poles of the system are calculated. The poles obtained by the deduced state space model and the poles obatined on the individual paths are compared.
Finally, the frequency response function is plotted to verify if the response obtained by the tfestimate() function and the responses for the state space and minreal transfer functions match.
The state space model developed is saved into a mat file.

In the second part of the project, the objective is to develop a state-feedback controller for the system. 
The state space model developed in the previous phase is validated in the time domain first.
The open loop system is tested to check whether it is completely observable and controllable throughout its states.
The state feedback gain matrix is obtained using a Linear Quadratic Regulator(LQR) function. The gain matrix is designed for the following conditions to meet.

Simulation Test Conditions:
• Choose zero initial conditions for the model at t=0; however, you are not allowed to reset the state initial conditions back to zero for any time after t=0
• Hold the excitation constant at u=4 for the first 10 ms of the simulation. Note that this first interval of time is required to demonstrate the open-loop response to a constant excitation
• At time t = 10 ms, apply your LQR full state feedback control law to the model, assuming you have complete knowledge of the state vector. Do NOT use a state estimator! You can NOT use any Matlab simulation functions such as lsim.
• Terminate your simulation at t = 30 ms

Mandatory Performance Requirements:
• The control signal must always be bounded within the saturation limits of ±10V
• All responses must always be bounded within the saturation limits of ±10V
• All responses must be settled to within ±0.5V after t = 20 ms.

The state vector is estimated using the Kalman filter. The gains obtained by the kalman filter are used to represent the complete feedback controller as follows. 
The discrete time output feedback system is given by the following matrices:
A = A_ss * K*C_ss
B = [(B_ss - K*D_ss) K]
C = -G
D = 0

The closed loop responses are plotted to compare the response with the actual responses. 

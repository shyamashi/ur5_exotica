### ur5_exotica: Procedures to adopt exotica motion planner with other robots
exotica motion planning package for ur5 robot
[Exotica Github](https://github.com/ipab-slmc/exotica)
### To draw the figure 8
1. Add the following lines in ```python_ik.launch``` with appropriate urdf and srdf of your robot replacing
the existing robot description

``` <param name="robot_description" textfile="$(find ur5_exotica)/resources/robots/ur5_robot.urdf" /> ```
``` <param name="robot_description_semantic" textfile="$(find ur5_exotica)/resources/robots/ur5_robot.srdf" /> ```

2. In ```example_ik.xml``` change 

  * ``` <JointGroup>manipulator</JointGroup>```. Here 'manipulator' is the planning group name described in the ur5_robot.srdf file
  * ``` <URDF>{ur5_exotica}/resources/robots/ur5_robot.urdf</URDF> ```
       ```<SRDF>{ur5_exotica}/resources/robots/ur5_robot.srdf</SRDF>```
  * end-effector link name ```  <Frame Link="ee_link" LinkOffset="0 0 0 0.7071067811865476 -4.3297802811774664e-17  0.7071067811865475 4.3297802811774664e-17"/>```
  * UR5 is a 6 DOF. Hence
      ``` <StartState>0 0 0 0 0 0 </StartState> ```
      ``` <NominalState>0 0 0 0 0 0</NominalState> ```
      ``` <W> 6 5 4 3 2 1 </W> ```
      
3. In ``` example_ik.py ```, ```q = array([0.0] * 6)``` for 6DOF
4. ``` roslaunch ur5_exotica python_ik.launch ```

  

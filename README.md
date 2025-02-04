# IoT-Enabled-Fall-Detection-System
This project proposes an IoT based fall detection and rescue system. The main objective here is to alert the guardian/ doctor if there is a possibility of fall. Therefore, it is designed in such a way that if an obstacle is sensed by the ultrasonic sensor then it alerts the user via a buzzer and hence will be saved from any accident / falling.Further, The most life-threatening aspect of falling is lying on the floor for long periods of time without any medical aid. If the distance between the obstacle and the sensor further reduces, then an email is sent to a specified email addess. Thereby preventing fall.


Software Requirements
Download and install the Proteus software.
Dowload and install Arduino IDE.
Download a virtual Serial Port Emmulator. [VSPE (64 BIT) is used for this project]
Required devices on proteus
ARDUINO UNO
LCD 16X2
L293D [MOTORDRIVER]
DC MOTORS
ULTRASONIC SENSOR
POT-HG
BUZZER
COMPIM
SETUP
Download the Blynk app on mobile from playstore.

Create an account and a new project by mentioning the device as Arduino instead of ESP module which is the default device.

After creating the project an email will be sent to the registered email address which contains the auth key.

This auth key needs to be copied and pasted in the Arduino code
char auth[] = "XXXXXXXXXXXXXXXXX";
to establish a connection between the circuit and the Blynk app.

Open Virtual Serial Port Emmulator.

Click on Add new device icon.

Select the option pair from dropdown under the device type. Click next.

image

Open the virtual serial port emulator and select device type as pair and click next which directs to select a pair of COMx and COMy.
Select COM1 from 1st list and COM2 from 2nd list and click Finish. This is done to establish a communication as shown below.

image

A window appears as shown below on successful connection

image

Edit the component - Ultrasonic Sensor

Download the ultrasonic sensor library for proteus via web search.
Three files can be found in the folder after extracting.
UltrasonicTEP.IDX,
UltrasonicTEP.LIB,
UltrasonicTEP.HEX.
Place these three files in the LIBRARY folder of your Proteus software folder. Sometimes LIBRARY folder can be found inside the DATA folder of the proteus as shown below
[...\Labcenter Electronics\Proteus 8 Professional\DATA\LIBRARY\UltraSonicSensor.HEX].
Download and Open the FALL DETECTION.pdsprj file on Proteus software.

Now, double click on the ultrasonic sensor, edit component dialog box appears.

In the ultrasonic sensor field. There is an option to select file. Select UltraSonicSensor.HEX file from the LIBRARIES folder of proteus. Click OK.

Double click on the COMPIM device and in the physical port select COM2 and set the Physical baud rate and virtual baud rate to 9600 from the dropdown. Then click okay.

image

Now, open command prompt and type the following 3 commands to communicate between the devices.

To Specify the appropriate path of the scripts folder of Blynk
cd C:\Users\HP\Documents\Arduino\libraries\Blynk\scripts.

Copy the blynk-ser.bat from the directories displayed.
dir

Now the device at COM1 is connected to Blynk cloud.
blynk-ser.bat -c COM1

Now, Download and open the Fall detection arduino.ino file from repository.

Click on FILE > PREFERENCES
This opens a dialog box, if the verbose output during compilation check box is unchecked then check the text box and click okay.

Now, run the Arduino file.
After compilation, the path of .hex file can be found as shown below

image

Copy the path of that file and go to proteus and double click on Arduino and paste the .hex file link in the program file section of arduino.

Now simulate the circuit in proteus and use POT-HG (+ and -) to vary the distance.

Adjust the distance using potentiometer, If the distance (cm) becomes < 390 then an email is sent to the email mentioned in the arduino code.

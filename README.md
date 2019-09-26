# Data Logger (and using cool sensors!)

*A lab report by Samson Schirmer.*

## In The Report

Include your responses to the bold questions on your own fork of [this lab report template](https://github.com/FAR-Lab/IDD-Fa18-Lab2). Include snippets of code that explain what you did. Deliverables are due next Tuesday. Post your lab reports as README.md pages on your GitHub, and post a link to that on your main class hub page.

For this lab, we will be experimenting with a variety of sensors, sending the data to the Arduino serial monitor, writing data to the EEPROM of the Arduino, and then playing the data back.

## Part A.  Writing to the Serial Monitor
 
**a. Based on the readings from the serial monitor, what is the range of the analog values being read?**
 
 0 - 1023
 
**b. How many bits of resolution does the analog to digital converter (ADC) on the Arduino have?**

10 bit

## Part B. RGB LED


**How might you use this with only the parts in your kit? Show us your solution.**

[Video Here] (https://github.com/sas695/IDD-Fa19-Lab3/blob/master/RGB%20LED.mov)

## Part C. Voltage Varying Sensors 
 
### 1. FSR, Flex Sensor, Photo cell, Softpot

**a. What voltage values do you see from your force sensor?**

0 - 1000

**b. What kind of relationship does the voltage have as a function of the force applied? (e.g., linear?)**

The relationship is exponential growth, in that the voltage jumps very high with a small force and is hard to get any more voltage by pressing very hard. 

**c. Can you change the LED fading code values so that you get the full range of output voltages from the LED when using your FSR?**

By diconnecting individual resistors I can change the color of the LED that is fading. 

**d. What resistance do you need to have in series to get a reasonable range of voltages from each sensor?**

10k ohm 

**e. What kind of relationship does the resistance have as a function of stimulus? (e.g., linear?)**

Similar to the FSR, the relationship for the bend sensor is nonlinear, in that the voltage jumps very high with a small bend and is hard to get any more voltage by more severe bending. The voltage increases with bend in one direction (up to about 300) and voltage decreases (down to about 45) with bend in the opposite direction. Without any bend, the voltage value on the serial plotter is around 206.

[Video Here] (https://github.com/sas695/IDD-Fa19-Lab3/blob/master/bend%20sensor.mov)

For the photocell, the more light the photocell recieves, the more voltage. 

And for the the slide sensor, sliding in one direction increases the voltage linearly and sliding the other direction decreases the voltage linearly. 

[Video Here] (https://github.com/sas695/IDD-Fa19-Lab3/blob/master/slide%20sensor.mov)

### 2. Accelerometer
 
**a. Include your accelerometer read-out code in your write-up.**

[Code Here] (https://github.com/sas695/IDD-Fa19-Lab3/blob/master/Accelerometer_Readout_.ino)


## Part D. Logging values to the EEPROM and reading them back
 
### 1. Reading and writing values to the Arduino EEPROM

**a. Does it matter what actions are assigned to which state? Why?**

Yes:
State 0 clears memory
State 1 reads the memory
State 2 writes the memory.

**b. Why is the code here all in the setup() functions and not in the loop() functions?**

Each character in the string is a byte. That is, it takes 8-bits to encode a character, so the number of characters in the string we are writing is the number of bytes we are occupying in EEPROM. The Atmega 328P at the heart of the Arduino has 1024 bytes of internal EEPROM Memory (which is separate from the 32KB of Program memory it has for the code it is running.)

**c. How many byte-sized data samples can you store on the Atmega328?**

1024

**d. How would you get analog data from the Arduino analog pins to be byte-sized? How about analog data from the I2C devices?**

Divide by four.

**e. Alternately, how would we store the data if it were bigger than a byte? (hint: take a look at the [EEPROMPut](https://www.arduino.cc/en/Reference/EEPROMPut) example)**

**Upload your modified code that takes in analog values from your sensors and prints them back out to the Arduino Serial Monitor.**

### 2. Design your logger
 
**a. Insert here a copy of your final state diagram.**

### 3. Create your data logger!
 
**a. Record and upload a short demo video of your logger in action.**

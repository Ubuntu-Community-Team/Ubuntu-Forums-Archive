---
title: "Device not working when /dev/ttyUSBx changes number (x changes)"
date: 2015-01-15
forum: Hardware
---

### Post by MacadamianNut on 2015-01-15
Hello. I'm working with a Darwin-OP robot which has Ubuntu 9.10 onboard. There is a subcontroller in the robot, the cm730, that is used to control the LEDs, motors, and additional sensors of the robot in its various programs to make the robot move around and generally be interactive. In order to write a custom program that utilizes the subcontroller, the following lines are used to initialize the connection

LinuxCM730 linux_cm730("/dev/ttyUSB0");
CM730 cm730(&linux_cm730);
if(cm730.Connect() == false)
{
      printf("Fail to connect CM-730!\n");
      return 0;
}

For some unknown reason, ttyUSBx has been changing randomly while working with the robot, both before execution of code and between executions. This is undesirable for the robot because it disconnects the cm730 subcontroller, making anything that relies on it unresponsive. 

I run the following command to check which number ttyUSB is active prior to running the program

ls -al /dev/ttyUSB*

Output from this is

crw-rw-rw- 1 root dialout 188, 1 2015-01-15 15:15 /dev/ttyUSB1 (where of course, that USB1 could change to anything from 0-9). 

If the number matches what's in the above code, the robot works fine when you run code until it changes again for some reason.

I was looking online for a solution for this and one suggestion was to create a symbolic link in the [COLOR=#333333][FONT=sans-serif]/etc/udev/rules.d/50-udev-default.rules [/FONT][/COLOR]file. However, I have no idea how to do this, and I don't even know how dialout comes into play in this problem when I thought it would be a device-specific problem. Checking the [COLOR=#333333][FONT=sans-serif]/etc/udev/rules.d/50-udev-default.rules[/FONT][/COLOR] file brings up the following as partial text

# serial
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"
KERNEL=="ppp",			MODE="0600"
KERNEL=="mwave",		GROUP="dialout"
KERNEL=="hvc*|hvsi*",		GROUP="dialout"
KERNEL=="ttyUSB[0-9]*",		MODE="0666"

Using lsusb to find out more about the device brought up

Bus 003 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:080a Logitech, Inc. 
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I think the related device is the first one listed (Ralink appears to be wifi related and I don't know what the Logitech device is). So basically, I was wondering what I could do to resolve the issue of the subcontroller disconnecting whenever /dev/ttyUSBx changes where x ranges from 0-9. I am fairly new to Linux and have never used udev nor am I very familiar with dialout other than adding a user to the group when I am blocked from serial communication. I would appreciate any help on this, thank you.

---


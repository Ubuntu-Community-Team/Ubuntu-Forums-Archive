---
title: "Configure ttyUSB0"
date: 2011-10-03
forum: Hardware
---

### Post by scurtsin on 2011-10-03
Ubunutu Kernel 2.6.32
 
First, I'd like to aplogize as my terminology is going to sound very Windows/DOS like. I'm just not sure how to convey what I'm trying to accomplish any other way. 
 
I have a device that has a physical USB plug however it is seen as a serial device by the OS. So essentially it's a USB Serial device. I need this device to appear a certain way on the Linux workstation as it is going to map to a Citrix Windows Server to access a published application. 
 
In linux, I was able to successfully configure this as ttyUSB0 by using the below command.
 
sudo modprobe usbserial vendor=0x0c27 product=232a
 
I then create symbolic link to ttyS03 using the below command. 
 
ln -s /dev/ttyUSB0 /dev/ttyS03
 
On the Citrix server (windows server 2003) I then map COM4 and the device is able to communicate from the workstation running Linux all the way to the session which is established on the Citrix Windows Server. 
 
Okay, so my question is how do I create a symbolic link in Linux to another ttyS other than ttyS03. Instead of ttyS03 I need to map this device in Linux to the equivalent of what would be COM Port 8 in Windows. Is this even possible?

---


---
title: "I'm unable to run an rs232 modem with usb adapter"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by doxelupo on 2005-09-09
I just installed Ubuntu 5.04 on my notebook, And I got an rs232 modem. 

My notebook  isn't provided with an rs232 connector so  I had to buy an rs232 to usb adapter: this one
 [http://www.digitus.info/scripts/digdetail.asp?artnr=DA-70145](http://www.digitus.info/scripts/digdetail.asp?artnr=DA-70145)
 it is based on the FTDI FT232 chip, and it should be supported in linux .

In the device manager with the adapter connected to the USB appears an rs232 device under an usb branch.  
The problem is that I'm unable to detect the modem when connected to the adapter. What would you suggest to solve this problem?
thank you for the help

---

### Post by mlomker on 2005-09-09
Do you know that the combination works under Windows?  I ask because some serial adapters do not properly implement the full serial spec.

How are you trying to connect to it?  Are you using minicom and typing AT commands to it?

If you type **dmesg** in a command prompt (after inserting the adapter) it should tell you what device it is being attached to.  Mine is /dev/ttyUSB0.  I just use mine for configuring routers, not a modem, but the principle is the same.

---

### Post by doxelupo on 2005-09-09
[QUOTE=mlomker]Do you know that the combination works under Windows? 

 I installed the combination of adapter and modem in windows and it was correctly recognised...I didn't try to connect me that way, I'm going to do it

How are you trying to connect to it?  Are you using minicom and typing AT commands to it? 
I've found minicom and now I'll install it 

If you type **dmesg** in a command prompt (after inserting the adapter) it should tell you what device it is being attached to.  Mine is /dev/ttyUSB0. 
I tried but as a reply I receive command not found. Do I have to install some diagnostic tool for it?


At present I just used the automatic modem search tool in ubuntu. I don't know anything on this subject.

---


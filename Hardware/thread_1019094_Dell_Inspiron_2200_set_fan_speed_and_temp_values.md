---
title: "Dell Inspiron 2200 set fan speed and temp values"
date: 2008-12-22
forum: Hardware
---

### Post by Eklod on 2008-12-22
I am running Ubuntu 8. X Hardy on my Dell Inspiron 2200.  My hardware seems as happy as I am, although things get hot at times!  - (This forum has been very helpful and a great source of information.)   

The fan kicks in at what seems to be half speed, when temp reaches 65 Celcius and stops when cooled to 50C.  

I would like to change these values to have the fan kicking at full speed if temp goes above 45C, 
and also have the fan half speed when temp is between 35-45 celcius 

This would replicate the configuration which I was running while using XP to keep things cool!  I was running something called fanGui, as BIOS does not have any functionality to control temp. I tried to set this up under Ubuntu without success so far.  I loaded lm-sensors.  Obtained an error message that temp sensor is not detected and also a warning about voltage.   Then I found and installed gkrellm.  At least I am now getting a temp reading, but still no control over the values that are used. Under Sensors, Fan and Voltage options are greyed out.  How and where do I specify the temp and fan speed?

Thank you for taking the time to read and assist with this.

---

### Post by linux_tech on 2008-12-22
check this-
[http://ubuntuforums.org/showthread.php?p=3237885](http://ubuntuforums.org/showthread.php?p=3237885)
this may also help:
[http://manpages.ubuntu.com/manpages/intrepid/man1/gkrellm.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/gkrellm.1.html)
[http://manpages.ubuntu.com/manpages/intrepid/man1/i8kmon.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/i8kmon.1.html)

---

### Post by Eklod on 2008-12-23
Problem resolved........ by simply adding a chekmark under gkrellm / Config /Plugins/DellI8kpluggin.  The tab where temperature values are defined appeared, both fans kicked in at full speed.  Enabling the plugging also added functionality to gkrellm in the form of manual controls for both fans.

---


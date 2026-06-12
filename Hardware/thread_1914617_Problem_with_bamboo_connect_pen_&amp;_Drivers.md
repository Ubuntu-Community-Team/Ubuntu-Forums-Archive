---
title: "Problem with bamboo connect pen &amp; Drivers"
date: 2012-01-24
forum: Hardware
---

### Post by grimslider75 on 2012-01-24
I follow Favux's instructions on [http://ubuntuforums.org/showthread.php?t=1515562]("http://ubuntuforums.org/showthread.php?t=1515562") and every goes well and dandy. Pressure sensitivity and everything works as expected within MyPaint. 

The problem: the tablet doesn't work after a reboot or two after the drivers and etc are installed via the aforementioned instructions. 

How I deal with it: I re-install the drivers.

The REAL problem: when I am at school or elsewhere with the bamboo tablet, I have no internet connection and therefore cannot go back and install the drivers. 
     In addition, I have no clue why I must keep going back to install the same exact drivers. How do they disappear or fail to work?

Ps. I am still a ubuntu noob because I haven't taken the time to learn the ins-and-outs of this beautiful operating system. 

Thanks In Advance! :D

---

### Post by Favux on 2012-01-24
Hi grimslider75,

> The problem: the tablet doesn't work after a reboot or two after the drivers and etc are installed via the aforementioned instructions.

That's a new one on me.  I wonder if somehow the wacom.ko is intermittently failing to auto-load.  Then when you recompile the *sudo depmod -a* command "fixes" it for a bit.  You could diagnose that by running:
```
lsmod
```
in a terminal after you recompile and reboot.  You should see *wacom*, which is the wacom.ko, in the list of loaded modules.  Then when the tablet stops working run lsmod again and see if *wacom* disappeared.  Or another way to diagnose that would be to just go straight to the fix.  Add ***wacom*** to the modules file in /etc:
```
gksudo gedit /etc/modules
```
and reboot.  That will "force"  the wacom.ko to be auto-loaded.  If that fixes the situation then auto-loading was the problem.

---

### Post by grimslider75 on 2012-01-25
> **Favux said:**
> Hi grimslider75,


That's a new one on me.  I wonder if somehow the wacom.ko is intermittently failing to auto-load.  Then when you recompile the *sudo depmod -a* command "fixes" it for a bit.  You could diagnose that by running:
```
lsmod
```
in a terminal after you recompile and reboot.  You should see *wacom*, which is the wacom.ko, in the list of loaded modules.  Then when the tablet stops working run lsmod again and see if *wacom* disappeared.  Or another way to diagnose that would be to just go straight to the fix.  Add ***wacom*** to the modules file in /etc:
```
gksudo gedit /etc/modules
```
and reboot.  That will "force"  the wacom.ko to be auto-loaded.  If that fixes the situation then auto-loading was the problem.

Thank you for helping me out once again! Your solution is correct and I thank you for your considerate effort to help me and many others. Thank you very much!

Kurt G
:popcorn:

---


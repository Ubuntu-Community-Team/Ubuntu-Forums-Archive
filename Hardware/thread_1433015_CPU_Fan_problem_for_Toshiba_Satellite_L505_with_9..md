---
title: "CPU Fan problem for Toshiba Satellite L505 with 9.1"
date: 2010-03-18
forum: Hardware
---

### Post by cbecker78 on 2010-03-18
I was wondering if there is a better solution to getting the fan to work properly with my laptop... I have seen several posts, with everyone doing slightly different things and  reporting slightly different results (even when doing the same thing???) And being a complete linux newby, I'm pretty lost.

I have version 9.1 of Ubuntu, upgraded from a 9.04 install- so it is still the older version of grub.
It is a Insyde H2O BIOS

(1) Default fan behavior is it will not come on unless I open the ubuntu software center , then it comes on full blast and will not turn off.  Monitoring temperature is impossible.

(2) doing "sudo apt-get install acpi" allows temperature of CPUs to be checked from command line, but fan will not come on no matter what after that is installed.  I just get to watch my processor temp creep up until I panic around 70 C and restart with Windows 7 so the fan will come on and cool it down.

(3) adding acpi_osi="Linux" to /boot/grub/menu.lst on the appropriate line (coresponding to the kernel I boot) AND haveing acpi installed will start the fan on some low speed at cold boot, and it will stay on continuously at that speed.   However, the fan will turn off upon hibernation, and not turn back on again after that unless the laptop is restarted.

---
I don't even know what acpi is.  I only know that the fan works fine under windows 7, and after all of the hard work I have put in over the last week and a half to get everything else on my laptop working with Ubuntu and getting all the custimization done to my tastes, it make me really sad to think all is for not because I can not get the propper behavior out of the fan.

Is there anyone that has the "right" way to fix this issue??? 

-Sorry for the somewhat lengthy post

---

### Post by cbecker78 on 2010-03-19
Anybody?

Update on what I have tried:

from (3) above, I installed lm-sensors and the applet. ran the auto setup, and rebooted my computer.  Fan was off.  put the sensor in the taskbar, watched the temp creep up.

at  55 C fan came on, at 47 C fan went off.  Did this all day  UNTIL I rebooted the computer.  Then the fan never came on again until I removed lm-sensors and rebooted.  reinstalling again does not bring back previous fan operation.

but this does indicate it "MUST" be possible to control the fan... somehow... right???

---

### Post by cbecker78 on 2010-03-19
There seriously needs to be a "how to screw around with your OS for newbies" instructional somewhere...  Or maybe there is and I just didn't look closely enough.

So here is the final report:

Everything I was observing was just coincidental, or accidental, or a fluke, or some combination of all of those.  The only thing that was happening was the fan was comming on low speed during the bios screen and staying on IF the processor was already hot (>34ish C). from a cold boot (~26-27 C fan stayed off).

what didn't i do?  

```
sudo update-grub
```Not sure if the first part of below is necessary, but to fix the problem (in case someone else is having this issue), these are the ultimate steps from a fresh OS install (9.04 upgraded to 9.1 via update) that fixed my fan issue.


```
sudo apt-get install lm-sensors sensors-applet
sudo sensors-detect
```accept all default categories, and manually insert core temp into /etc/modules file with gksudo gedit /etc/modules

reboot, right-click on panel, add hdd temp applet to panel to monitor temp

reading system message log, i always see a message stating that driver for core temp not found... so this probably doesn't matter.

following code/steps is what got the fan going
```
gksudo gedit /boot/grub/menu.lst
```and add acpi_osi="Linux" to end just after "quiet splash" corresponding to kernel I boot.

something like /boot/vmlinuz-2.6.28-11-generic root=[lots of numbers and text] 

then ```
sudo update-grub
``` and reboot

then reboot and fan comes on at 54C and off at 47 C.

Note: I am using the old version of grub.  I also don't know if these temps are good, but at least fan is working.

Edit:  Quirks/bug-  comming out of hibernation, fan will come on at low speed and stay on.  Will resume normal behavior on full reboot.

---

### Post by jinchuricki on 2011-12-05
Hi. I just find the trick to solve this problem. 
I have wrote it in my blog.
[http://jinchuricki.blogspot.com/2011/11/solution-how-to-fix-toshiba-laptop-fan.html](http://jinchuricki.blogspot.com/2011/11/solution-how-to-fix-toshiba-laptop-fan.html)

I hope it works too in your laptop. :popcorn:

---


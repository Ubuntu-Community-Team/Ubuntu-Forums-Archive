---
title: "Acer Travelmate old laptop issue in Shutdown/Restart"
date: 2014-07-16
forum: Hardware
---

### Post by gigi3 on 2014-07-16
Hi all, I just successfully installed Ubuntu 14.04 on my old Acer Travelmate 2420 laptop alongside Windows XP Home (my thread [here]("http://ubuntuforums.org/showthread.php?t=2233854")). However, I got an issue related to my laptop powering off. Using both Shutdown and Restart commands cause the notebook to stop its activity and it doesn't power off or reboot effectively. Pressing Ctrl-Alt-Backspace to look at the console messages the last lines looks like:
```
* Deactivating swap ... [OK]
* Unmounting local filesystem ... [OK]
* Will now halt

```
after Shutdown command and
```
* Deactivating swap ... [OK]
* Will now restart

```
after Restart. So, to power off the computer completely I have to hold down the on-off button for 4-5 seconds, or disconnect the power source cable (the battery is dead, I don't use it anymore). Similar behaviour with the liveCD where the system opens the drive door and wait for an Enter keypress but this keypress has no effect. May be an hardware problem, I don't know, but in Windows both commands work as espected. I was wondering if someone here has got the same or similar issue. Cheers
Gigi
PS: 'sudo shutdown -r now' doesn't solve the issue ...

---

### Post by gigi3 on 2014-07-21
I have also tried changing Wake On Lan bios option but no effects. Any suggestion? At least to correctly reach the 'System halted' message ... thanks

---

### Post by Zorrothustra on 2014-09-29
Hi Gigi3, having exactly the same issue here on another laptop. Did you ever find a solution ?

---

### Post by gigi3 on 2014-09-30
Hi Zorrothustra, no unfortunately no solutions at this time, I still have to power off manually ...

---


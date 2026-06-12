---
title: "Sony VPCY2, Brightness problem (14.04)"
date: 2014-04-22
forum: Hardware
---

### Post by deenoo-g on 2014-04-22
Unfortunateley Taz's solution stopped working  (since upgrading to the latest 14.04) ... using Vaio VPCY2.
Does anyone have a fix for this ?

---

### Post by Toz on 2014-04-22
*Moved post to its own thread. From: [http://ubuntuforums.org/showthread.php?t=2086359]("http://ubuntuforums.org/showthread.php?t=2086359")*

Hello and welcome to the forums. 
Lets start from the beginning. Can you please post back the results to the following commands?

1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
4. A listing of your loaded kernel modules:
```
lsmod
```
5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---


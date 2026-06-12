---
title: "Windows XP have lower fan speed then Ubuntu"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by SpinningAround on 2008-03-26
I use a dual boot with Windows XP and Ubuntu 7.10 (stationary not the laptop in sign), when i'm in XP is the CPU fan speed according to CoreCenter a little less then 2000 rpm while idle. Strange thing is when i check the CPU fan speed with sensors is the speed over 3000 rpm this do create some extra sound, yes the temp is lower in ubuntu but the temp is nothing to worry about when the computer is idle. So is it some way possible to slow down the fan speed a little.

---

### Post by non-poster on 2008-03-26
fancontrol, part of lm-sensors

---

### Post by SpinningAround on 2008-03-27
I did run the command and got this message.

> 
:~$ sudo fancontrol 
Loading configuration from /etc/fancontrol ...
grep: /etc/fancontrol: File or catalog don't exist 
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
grep: /etc/fancontrol: File or catalog don't exis
Some mandatory settings missing, please check your config file!


---


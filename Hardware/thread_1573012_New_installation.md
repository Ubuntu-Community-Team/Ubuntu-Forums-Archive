---
title: "New installation"
date: 2010-09-12
forum: Hardware
---

### Post by Flipper_Al on 2010-09-12
Hi
Emachines M5116 laptop, dual boot XP/Ubuntu, xp boots fine, Ubuntu, just hangs with a black screen, if i start in failsafe mode its fine even have the wireless working......any ideas

Cheers:D

---

### Post by dino99 on 2010-09-12
look at driver activation: system admin additional drivers

which graphic or chipset is used on your system ?

---

### Post by sikander3786 on 2010-09-12
I think it is using the Intel Extreme Graphics Chipset. Try to boot into recovery mode and select "reconfigure graphics" or something like that.

---

### Post by Flipper_Al on 2010-09-12
> **sikander3786 said:**
> I think it is using the Intel Extreme Graphics Chipset. Try to boot into recovery mode and select "reconfigure graphics" or something like that.
 
 
Intel extreme
Intel 82852/82855 GM/GME graphics controller
 
Like i said all good in recovery mode, its just when i select the normal boot it hangs with a blank screen

---

### Post by sikander3786 on 2010-09-12
> **Flipper_Al said:**
> Intel extreme
Intel 82852/82855 GM/GME graphics controller
 
Like i said all good in recovery mode, its just when i select the normal boot it hangs with a blank screen
Have you tried reconfiguring graphics and then rebooting in normal mode?

---

### Post by Flipper_Al on 2010-09-13
Bit more info, 
Check the /etc/var/syslog and on normal boot nothing is being written into the logfile
On a failsafe loads of info in the log file
Does a normal system startup write anywhere else, on bootup.....?

---

### Post by efren386 on 2010-09-13
same with me what i did at grub menu add nomodeset after the quite parameter

---

### Post by sikander3786 on 2010-09-14
Press and hold down the Shift key as soon as your computer gets past the BIOS screen. Grub menu will pop up. Select the top most entry and press "e" to edit it. Using arrow keys navigate to the the words "quiet and splash", delete them and type "i915.modeset=0 xforcevesa" in their place. Press Ctrl and X to boot.

If "i915.modeset=0 xforcevesa" doesn't work, try "i915.modeset=1". See this thread for additional details.

[http://ubuntuforums.org/showthread.php?t=1475128](http://ubuntuforums.org/showthread.php?t=1475128)

---


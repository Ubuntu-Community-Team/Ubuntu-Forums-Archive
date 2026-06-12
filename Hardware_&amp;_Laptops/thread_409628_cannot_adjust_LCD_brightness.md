---
title: "cannot adjust LCD brightness"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by jiasheng on 2007-04-14
I cannot adjust the brightness either with the Fn keys or with gnome-power-manager.  Actually, I cannot even find a brightness slider in gnome-power-manager, however, the screen becomes dimmer when using battery than when using AC power.  So I think there is sort of control that the system can do with the brightness of LCD.  Is there any way that I can adjust the brightness of the LCD in different levels?  Thanks.
Laptop model: HP dv2210us
System: Ubuntu Feisty beta
Kernel: 2.6.20-15-generic

---

### Post by pingpongboss on 2007-04-14
try gconf and look under apps, gnome-power-manager

i'm not entirely sure but i think the xx_brightness keys can be set to achieve different brightness values (default looks to be 100)

too bad i have a toshiba laptop with a BIOS which only works with windows.. can't get brightness to change at all..

---

### Post by jiasheng on 2007-04-14
Thanks for the reply.  I found the settings you mentioned in gconf-editor -> app ->gnome-power-manager.  Unfortunately, the modification of the ac_brightness values has no effect :(

---

### Post by jiasheng on 2007-04-19
I wanna up this to find out whether there is a solution, since the final of feisty has been released but it seems there is no new update for feisty beta.  I have also posted this question on the launchpad but got no reply yet.  Should this be considered as a bug of some kind?

---

### Post by Caligatio on 2007-04-22
I'm having this same problem with my ASUS Z71V.  The brightness keys don't do anything (they worked in 6.06/6.10) and the Power Manager brightness setting has no effect.

I'm stuck with an overly dark screen constantly :(

---

### Post by ivoks on 2007-04-23
Try 'sudo rmmod video' and then again. If that works for you, add

blacklist video

to /etc/modprobe.d/blacklist

---

### Post by jiasheng on 2007-04-23
> **ivoks said:**
> Try 'sudo rmmod video' and then again. If that works for you, add

blacklist video

to /etc/modprobe.d/blacklist

Unfortunately, that didn't work for me.  As I am trying Kubuntu now, the kpowersave reported that my hardware is not supported when I tried to adjust the brightness via it.  The only way now works for me is turn to /proc/acpi/video/VGA/LCD.  There are several levels of brightness in the file "brightness".  And the brightness can be adjusted by running "echo xx > brightness" under the directory as root and xx is the number of a certain level.

---

### Post by rosegarden78 on 2008-01-19
Try typing this command in a terminal
 
 xgamma -gamma 0.75
 
 I have posted my own solution here:
 
 [http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---


---
title: "Low max brightness on eee pc T101MT"
date: 2012-10-31
forum: Hardware
---

### Post by h2z on 2012-10-31
I've just recently installed Lubuntu 12.10 on my Asus eee PC T101MT laptop and the max brightness is only about 50% of what I get from windows. The VGA device on this laptop is the Intel GMA 3150. I installed the mesa drivers.

I can change the brightness using the FN key on my keyboard, and by installing xbacklight. I have tried xrandr but could not figure out what "crtc" is and how to use that. 

Is there any way to get the REAL max brightness?

---

### Post by Malexan on 2012-11-19
I found solution here: [https://wiki.archlinux.org/index.php/ASUS_Eee_PC_T101MT#Brightness](https://wiki.archlinux.org/index.php/ASUS_Eee_PC_T101MT#Brightness)

---

### Post by Rock Storm on 2012-12-09
> **h2z said:**
> I've just recently installed Lubuntu 12.10 on my Asus eee PC T101MT laptop and the max brightness is only about 50% of what I get from windows. The VGA device on this laptop is the Intel GMA 3150. I installed the mesa drivers.

I can change the brightness using the FN key on my keyboard, and by installing xbacklight. I have tried xrandr but could not figure out what "crtc" is and how to use that. 

I had exactly the same problem on an Asus EeePC 1015CX after installing Lubuntu 12.10.

I must say I haven't tried the solution given by Malexan, you should probably try that one first:
> **Malexan said:**
> I found solution here: [https://wiki.archlinux.org/index.php/ASUS_Eee_PC_T101MT#Brightness](https://wiki.archlinux.org/index.php/ASUS_Eee_PC_T101MT#Brightness)

What worked for me was this (please don't forget to read the *additional notes *below):[INDENT]Edit the file named "brightness" in /sys/class/backlight/psb-bl, where it said 0, just write e.g. 50. In order to modify this kind of files you need to be root, so open a terminal (*Accesories -> LXTerminal) *and proceed as follows:
```
cd /sys/class/backlight/psb-bl
sudo leafpad brightness
```To make this change permanent you must edit the file "rc.local" in /etc. Just like this:
```
cd /etc
sudo leafpad rc.local
```Where it says:[INDENT] exit 0
[/INDENT]Rewrite to (again, instead of 50 you can type any number between 0 and 100):[INDENT]echo 50 > /sys/class/backlight/psb-bl/brightness
exit 0
[/INDENT][/INDENT]Additional notes:

[LIST]
[*]If you don't see (or don't even have) the folder "psb-bl" or the above explained doesn't work, there is another "brightness" file in /sys/class/backlight/acpi_video0.
[*]Some authors suggest to comment out the "exit 0" (This would be, adding a # before it) Works likewise.
[/LIST]

---


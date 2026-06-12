---
title: "cannot edit certain system files"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by crag277 on 2006-10-27
I have a strange computer (MSI MEGA 865) that does not control the CPU fan speed through the BIOS.  Last Ubuntu I had on here was Breezy, and then, after I installed the lm-sensors package, I was able to manually change the speed of the fans by changing the integer value in the files "pwm1" and "pwm2" located at:

/sys/bus/i2c/devices/9191-0800

I just installed Edgy on this machine and tried to do the same procedure, except this time every time I try to edit these file I get a permission denied error.  Yes I am using "sudo".  I have tried gedit, vi, nano, and the echo command, but none will let me change these values.

Any ideas?

---


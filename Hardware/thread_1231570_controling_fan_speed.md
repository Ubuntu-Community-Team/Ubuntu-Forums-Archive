---
title: "controling fan speed"
date: 2009-08-04
forum: Hardware
---

### Post by privatejarhead on 2009-08-04
well...i have 9.04 installed on my toshiba satellite l505 and i like it, but the fan wont start up at all, especially when my laptop begins to overheat. this forces me to shut down after X number of minutes so that i dont fry my system. i looked up ubuntuforums for the solution and i found this article:

[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

i've followed it up to just after "sudo powersave -T", but i dont get a thermal device 1 or anything, only this:

Thermal Device no. 0:
Temperature: 53
Critical: 114
Passive: 114
Active 0: 70

then after that when i try the cat code, i get this:

cat: /proc/acpi/thermal_zone/TZ1/trip_points: No such file or directory



any help on how to get this process to work with me? is there another way to allow me to control my laptop's fan (like something i can install, preferably with a GUI interface, but i can work with CLI)?

thanks in advance

---

### Post by Yellow Pasque on 2009-08-04
Does your toshiba have a Phoenix BIOS? Maybe the omnibook module would help? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021)

---

### Post by privatejarhead on 2009-08-05
nah, it has some other bios. its something h20 or somewhere along the lines of that. ill post when i find out


EDIT: I have an InsydeH20 BIOS.

---


---
title: "Built in webcam problems !"
date: 2010-09-30
forum: Hardware
---

### Post by UldiZ on 2010-09-30
I has changed my OS from XP to Linux Ubuntu 10.04 and found that webcam on my laptop is not working now. I have Asus Z99L series laptop and system is recognized it ( typing in terminal- lsusb) as ; Bus 001 Device 002: ID 174f:aa11 Syntek Web Cam, but it does'nt work. Can somebody help to solve this problem ?

---

### Post by ajgreeny on 2010-09-30
How have you been testing the webcam?

If you have not already done so, try using cheese, and wxcam, both available in the repos.  If you have simply been trying skype, you may neet to add an option to the skype startup command to get the webcam working.

Try the command ```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```which is for a 32 bit system; if you have a 64 bit OS you will need to edit it slightly as the library file is in another folder (/usr/lib64/libv4l/v4l2convert.so) or something like that; search around, I think you'll find it.

---

### Post by jaesjg on 2010-10-09
Bump. 
My integrated webcam on a Compaq CQ40 was working fine on karmic, and even in the early days of lucid, but now Cheese has decided that there's no camera, and lsusb does not show any camera either.

---


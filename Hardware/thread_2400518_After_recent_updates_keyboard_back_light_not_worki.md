---
title: "After recent updates keyboard back light not working"
date: 2018-09-06
forum: Hardware
---

### Post by curtbroo on 2018-09-06
Hello,

I have a Sony Vaio model SVE171C11L. I am currently running Ubuntu 16.04 LTS 64-bit.

A few months ago, after an update to my operating system, my keyboard backlighting stopped working.

When I boot the computer, the backlight comes on (I imagine that it is part of the system boot test) but when Ubuntu comes up, no more backlighting.

I have searched the forum and found other, seemingly helpful solutions and I've tried them all, but none of them worked.

I have tried the following with both the backlight and the backlight_timeout options:
sudo modprobe -r sony_laptop
sudo modprobe -v sony_laptop kbd_backlight=0I've also tried:
sudo su -c "echo 1 > /sys/devices/platform/sony-laptop/kbd_backlight"
Is there something I am missing?

Also, is there a graphic utility that I can use to control this issue instead of the terminal?

cb

---


---
title: "/dev/nvidia0 permission and group keep changing"
date: 2009-01-21
forum: Hardware
---

### Post by RoyalPro on 2009-01-21
My /dev/nvidia0 keeps changing the group from "video" to "44" while I am using the computer trying to run UT2004.  If I just set permissions to 666 for it it changes them back too.  I can't create a group "44" either.  Anyone have any ideas?

I am using NVIDIA-Linux-x86_64-180.17-pkg2 for my drivers, and  Ubuntu 8.10 64 bit.

---

### Post by RoyalPro on 2009-01-22
Got it working by changing the group id for video to 44.  The video group disappeared from the gui group list but now works with UT2004 and BOINC.

---

### Post by davygrvy on 2009-10-24
perfect!  thank you
$ sudo gedit /etc/group

---


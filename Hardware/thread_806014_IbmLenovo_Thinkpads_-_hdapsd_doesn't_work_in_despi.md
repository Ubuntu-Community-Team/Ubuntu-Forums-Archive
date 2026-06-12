---
title: "Ibm/Lenovo Thinkpads - hdapsd doesn't work in despite hdaps-gl working perfectly !"
date: 2008-05-24
forum: Hardware
---

### Post by Axx83 on 2008-05-24
I have filed a bug on launchpad about this: [Bug #234601]("https://bugs.launchpad.net/ubuntu/+source/hdapsd/+bug/234601") let me know if it works for you.

I have successfully loaded the tp_smapi and the hdaps_ec module in a Hardy installation on my Thinkpad X60s:

myname@myname-laptop:~$ lsmod
Module      Size   Used by
[...]
hdaps_ec    14556  0
tp_smapi    23952  0
thinkpad_ec 8464   2    hdaps_ec,tp_smapi
[...]

I install both the hdapsd packet and the hdaps-utils packet via synaptic, I reboot and i try to run the hdapsd deamon to protect my hard drive:

myname@myname-laptop:~$ hdapsd -d sda -s 15 -a
WARNING: Cannot open hdaps position input file /dev/input/hdaps/accelerometer-event (Permission denied). You may be using an incompatible version of the hdaps module, or missing the required udev rule. Falling back to reading the position from sysfs (uses more power). Use '-y' to silence this warning.
open(protect_file): No such file or directory

if I run it with sudo:

myname@myname-laptop:~$ sudo hdapsd -d sda -s 15 -a
Password or swipe finger:
open(protect_file): No such file or directory

but when I run hdaps-gl IT WORKS I can see the 3d image of my computer moving and the movement is perfect, totally calibrated.

In fact /dev/input/hdaps/accelerometer-event is actually present on my comp, because hdaps installed a udev rule that creates this sym link, the link is root only tough, probably that is why I can't access it without sudo.

---

### Post by bomanizer on 2008-05-25
I had to patch & compile the kernel to get parking to work. This was on Gutsy, seems that the issue is still persistent in Hardy.

Oh, another thing: I compiled the tp_smapi module also from source and created a .deb.

---

### Post by Axx83 on 2008-05-25
Yes I found out too that hdapsd is completely useless unless you patch the kernel...so long for an easy friendly os suited for casual users...at least they should say in the package description that it won't run at all.

The bug seems to be this one:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139881]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139881")

---


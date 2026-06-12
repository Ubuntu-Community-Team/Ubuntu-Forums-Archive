---
title: "nVidia drivers enabled, now ubuntu fails to boot!"
date: 2008-09-13
forum: Hardware
---

### Post by jon_fairley on 2008-09-13
First. I am a ubuntu noob, so please be patient with me (I know almost nothing about Linux). Since installing Ubuntu I have updated the system, and then went to enable my graphics card driver. (I run a nVidia 8600m GT) Ubuntu found the driver and downloaded it for me. I was then instructed to perform a restart, and ubuntu then failed to boot. Before the OS is up and running, I get 'snow' and am unable to do anything except turn off my computer, and reboot into Windows. Ubuntu doesn't work now.

How can I fix this problem, knowing that I can't get into the OS. Please describe anything I can do in great detail as I have about one hour of Linux experience and know next to nothing about it. 

Thanks for any advice.

---

### Post by DoctorMO on 2008-09-14
This help page in the wiki might be able to help you, it explains how to troubleshoot:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Common%20Problems](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Common%20Problems)

You can get to a command line by pressing [Ctrl]+[Alt]+[F1] and logging in at the prompt.

If you want to get back to a desktop then you can change the driver being used by x11 by editing the file /etc/X11/xorg.conf and looking for the part that says 'nvidia' and changing it to 'nv'

good luck.

---


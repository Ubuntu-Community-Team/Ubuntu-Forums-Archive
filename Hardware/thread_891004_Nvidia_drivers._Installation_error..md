---
title: "Nvidia drivers. Installation error."
date: 2008-08-15
forum: Hardware
---

### Post by kaldor on 2008-08-15
As root, I type:

root@Michael-Laptop:~# cd /home/michael
root@Michael-Laptop:/home/michael# sh NVIDIA-Linux-x86-100.14.09-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 100.14.09........................................................................................................................................................................................................................................................


After that, a message comes up and says   

ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).



How do I fix this? I really want to play some games, (old games, nothing new) and I need to use Linux because Vista is bugging up too much for me.

---

### Post by phidia on 2008-08-15
I don't know which version of Ubuntu you're using but do you get the choice to enable the nvidia driver from System > Administration >Hardware Drivers? That's the perferred way of getting the driver working.
There are more [detailed guides]("https://help.ubuntu.com/community/Video") at the Ubuntu wiki.

---

### Post by kaldor on 2008-08-15
I am using 8.04

I tried that driver thing, nothing there at all.

---

### Post by phidia on 2008-08-15
I don't know what card you have either-I should have asked but the [HOWTO here]("http://ubuntuforums.org/showthread.php?t=797270&highlight=nvidia+card") provides you with the command to stop the xserver > sudo /etc/init.d/gdm stop as well as a comprehensive nvidia install guide. Hope that helps.

---


---
title: "Kernel upgradation problem !!!"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by rajputrajat on 2009-02-23
I have Kubuntu 8.10 installed on my laptop with KDE upgraded to 4.2.
1) I am unable to upgrade the kernel on my system.
At this moment it's 2.6.27-7, when I try to upgrade it to *-11...
it doesn't give any error and gets installed.. 
but linux kernel image doesn't come in the boot folder (even boot options come in the grub for the new kernel).... :|

2) I have installed many softwares on the system and want to share the customized disk (with the help of remastersys) with my friends....
Now the problem is, if I make the disk..it doesn't boot...doesn't find kernel to boot (I think)...
I've already made the disks and installed them successfully...
(not remastersys problem)...

I think, there is some relation between both the problems!!!

---

### Post by ajgreeny on 2009-02-23
Checkwhether* /usr/sbin/update-grub* is executable.  I seem to remember a few cases where I have read that it is not always so, for some reason.  If it is not, then the kernel will install, but there will be no easy way to boot to it.

---

### Post by rajputrajat on 2009-02-23
thanks for the reply...
but, update-grub is already executable...
i've the working kernel...but i can't upgrade it...
and if I make remastersys copy..that doesn't boot...
any clues, guys???

---

### Post by rajputrajat on 2009-02-23
look into the /boot:
--------------------------------------
rajat@BLUeMoon:/boot$ ls -lh
total 16M
-rw-r--r-- 1 root root  497K 2009-01-30 02:41 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  496K 2008-11-05 02:30 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   90K 2009-01-30 02:41 config-2.6.27-11-generic
-rw-r--r-- 1 root root   90K 2008-11-05 02:30 config-2.6.27-7-generic
drwxr-xr-x 2 root root  4.0K 2009-02-23 23:22 grub
-rw-r--r-- 1 root root  7.9M 2008-11-29 02:54 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  122K 2008-09-12 01:41 memtest86+.bin
-rw-r--r-- 1 root root 1008K 2009-01-30 02:41 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1006K 2008-11-05 02:30 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root  1.1K 2009-01-30 02:42 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root  1.1K 2008-11-05 02:32 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root  2.2M 2009-01-30 02:41 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root  2.2M 2008-11-05 02:30 vmlinuz-2.6.27-7-generic
--------------------------------------------------------------------------

I just again upgraded to the 2.6.27-11
and "initrd.img-2.6.27-11-generic" file is missing..
all other files related to -11 are available.....

what should i do???

---

### Post by rajputrajat on 2009-02-23
got the solution for the first problem....

there was some syntax problem in the "/etc/initramfs-tools/conf.d/resume" file....
so whenever "update-mkinitramfs" command was running...
it was unable to generate the new initrd file....

I just deleted "\240(delete)"..from the "RESUME=/dev/sdc2\240(delete)"..
now, it's just..."RESUME=/dev/sdc2"...and working fine....

I have no idea..how it got changed, though....

i'll try to make the remastersys distro...and let you guys know the result...
:)

---

### Post by rajputrajat on 2009-02-24
Everything is working working now....
New remastersysed Disk is booting fine...

---


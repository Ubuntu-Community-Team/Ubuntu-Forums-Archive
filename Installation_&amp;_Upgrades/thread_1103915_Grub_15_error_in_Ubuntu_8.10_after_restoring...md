---
title: "Grub 15 error in Ubuntu 8.10 after restoring.."
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-03-23
the source of problem is due to my Makefile i created for my project....
It deleted /bin,/boot directories in root filesystem(as far as i know)
I have a 8.10 Live CD...
I formatted a Ubuntu 8.04 and installed 8.10 in a new PC..now same prob with another PC..I have many imp files here...


I copied the /bin,/boot dir from newly installed PC to my PC...I followed GRUB restoration using 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

i succeeded in that..but when i choose an option in my GRUB while bootin i get File not found(error 15)..

i didnt get any output when i typed root (hd0,0)...but i proceeded with that....

can someone help in editing this new menu.lst??

my fdisk output is 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f591f58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9357    75160071   83  Linux
/dev/sda2            9358        9729     2988090    5  Extended
/dev/sda5            9358        9729     2988058+  82  Linux swap/Solaris

---

### Post by vpnm_87 on 2009-03-24
Copied the bin,boot directories from another working PC....
Then installed grub as indicated in the post i mentioned...
Got Grub working but file not found error 15...
copied uuid value from /etc/fstab and pasted it in /boot/grub/menu.lst..
Finally made my PC up and running:)

---


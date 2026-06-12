---
title: "No Active Partition after a new 9.04 server install"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by ddevore on 2009-05-18
I am attempting to rebuild my server. I have 3 new drives one being for the OS and two for mirroring. I installed 9.04 amd64 server to the OS drive using LMV but after installing it is giving me "No Active Partition" when I try and boot. I have tried fixing it using grub and it gives me errors. 

First if I do 

fdisk -l

I get the OS drive listed as sdb with the Linum LVM listed as sdb1

NOTE: 
when I look at the drives in the bios I get the OS drive listed as the First SATA Master. 

I found this in another thread:

sudo grub
grub> find /boot/grub/stage1
[should return a partition in the form (hdX,Y), which should be your Ubuntu partition]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit


When I try this I get 

grub> find /boot/grub/stage1

- ERROR 15: File not found

grub> root (hdX,Y)

- Using sdb,1 I get Error 23: Error while parsing number


This is where I am currently. Please let me know if there is anything else I can do. By the way I am not dual booting and all the drives were new and clean when this process was started.


Thanks for any help/direction you can provide.

---


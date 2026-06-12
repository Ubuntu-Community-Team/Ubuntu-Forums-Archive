---
title: "Error 18 After Server Install"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Flappi282 on 2009-10-03
Hi. I am a newb at linux, because i have never worked with it before. but i can edit the BIOS and everything ok.
This computer has 1 new HDD, and NO DUAL BOOT
I just installed ubuntu server edition, which went well, except i couldn't connect via wi-fi. Didn't matter, moved on. I installed it on a new 200GB Maxtor hard-drive. I removed the old one, since my (really) old Pentinum III computer only had 1 3.5" Bay. The first time, the disc was scratched, and after partitioning, it brung up loads of package errors. I made a new disc, and the partitioner i think formatted the old partition and used that (I HAVE 1 PARTITION). After installing, i got a prompt to restart.
I did this, then afterwards i got this:
```
Verifying DMI Pool Data .........
Boot from ATAPI CD-ROM : Failure ...
GRUB Loading stage1.5
 
 
GRUB loading, please wait...
Error 18

```
And it hangs forever
Thanks in advance!

---

### Post by binary00mind on 2009-10-03
I have few questions. 
First how old is your computer? How big was your previous/old HD disk? and last but not least the layout of your new Ubuntu installation partitions is needed...like where is swap? home? and so on...
After that I tell you what to do.

I give a link to read about error 18, so you can guess by yourself what i have in mind... 
Here is a link: [url]http://wiki.linuxquestions.org/wiki/GRUB#Error_18

---

### Post by Flappi282 on 2009-10-04
My pentium 3 PC is about 6 years old
Specs:
512 mb ram
Pentium 3 Processor
Award BIOS
Energy* power unit.
 
 
 I just followed a tutorial in PCPlus to turn an old PC into a server. I tried to install it 3 times, and i think i accidently made 9 partitions in total :oops:
I just need something to reset the harddrive, and join all the partitions, format then i can reinstall.
Does anyone know of anything i can use to do this?

---

### Post by rreese6 on 2009-10-04
To help you with your problem, more information is needed.

1. Boot up with LiveCD. Once you are on the Desktop, got to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by binary00mind on 2009-10-04
With all respect to rreese6 idea which is in itself a good idea to gather more info. 

But one must understand the nature of grub error# 18 in principle. 

Flappi282 you can do this. It's very simple. You are very early in the game so you have nothing to loose. 
Reinstall Ubuntu and create partitions this way that the very first partition /sda1 is primary! 
With the mount point as /boot !!! 
between 2GB up to 6GB but no more then 8GB I would go with 4GB  

After that you can create other partitions like /home /root swap (and whatever is on your mind) anyway you like it.

---


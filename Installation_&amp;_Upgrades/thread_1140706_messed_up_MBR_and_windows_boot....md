---
title: "messed up MBR and windows boot..."
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Nighthawk4900 on 2009-04-27
Background:
I had windows xp pro working perfectly fine. Recently I got a CD for kubuntu 8.10 and I figured I'd try it out. I checked my partitions, and it turned out that I already had two partitions. One partition where windows was installed and then a smaller secondary partition that I wasn't really using before. I figured I'd install Kubuntu to that partition. Well I installed and everything worked fine... except for the fact that the Windows installation was not recognized by Grub and therefore I could no longer boot into Windows. I tried by adding an entry into the grub file for windows following suggestions from other forums where people had similar problems, but that didn't work either. I guess I got desperate at this point and tried a bunch of things, but nothing worked. 

I tried to use the XP recovery CD and it didnt even recognize my XP installation. i did something and now it does, however...it keeps asking for an administrator password, and says the pw I enter is wrong. Anyways...

I got Ubuntu to install and manually set the partitions. this is the fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

Device              Boot      Start         End      Blocks         Id     System
/dev/sda1             *           2          38764   293048280    f       W95 Ext'd (LBA)
/dev/sda5                          2          35217   266232928+   7    HPFS/NTFS
/dev/sda6                     35218       38506      24864808+   83  Linux
/dev/sda7                     38507        38764     1950448+     82   Linux swap/ Solaris
ubuntu@ubuntu:~$

```It should be noted, I was able to mount the ntfs partition and am able to access all of my data. Also, upon inspection of the NTFS partition, I noticed that the boot.ini file was missing??

also it might be worth noting that adding an entry into menu.lst for windows with root (hd0,4) gives me an error 12 when trying to boot...



I need to fix things so that i can boot right back into windows

any and all help will be appreciated!

---

### Post by Mark Phelps on 2009-04-28
Change your Windows XP menu.lst line to either root (hd0,0) or root (hd0,1).  One of them should work.

---


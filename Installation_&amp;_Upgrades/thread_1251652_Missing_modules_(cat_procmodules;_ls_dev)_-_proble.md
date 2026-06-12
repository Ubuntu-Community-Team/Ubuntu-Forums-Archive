---
title: "Missing modules (cat /proc/modules; ls /dev) - problem during boot os"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by emtec08 on 2009-08-27
Boot from (hd0,0) ext3 5108701a-641d-43b182eb-aeb6da348d62
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough ?)
- Check root = (did the system wait for the right device ?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/5108701a-641d-43b182eb-aeb6da348d62 does not
exist . Dropping to a shell!


Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

uname -a

Linux (none) 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC
2009 x86_64 unknown

below are system specification for this server:
1. intel(R) Quad Core E5506 Xeon(R) CPU,2.13GHz, 4M Cache, 4.86 GT/s QPI.
2. 2nd processor same.
3. Raid 1
4. 300GB 3.5-inch 15K RPM SAS Hard Drive
5. Ubuntu Server i386 9.04

please suggest me solution .....

---

### Post by stlsaint on 2009-08-27
is this off of a fresh install?

---

### Post by emtec08 on 2009-08-27
yes

---

### Post by kseise on 2009-11-02
Same exact problem here.  I tried a fresh install of 9.10 on a RAID 0 using software raid.  My RAID 5 /home array was picked up fine, but the RAID O root array could not be booted, and generated the same error message quoted above.

---

### Post by zarathustra on 2009-11-02
I have an identical problem. I have two SATA drives, no RAID though. Worked fine in 9.04, boots into grub then crashes as above.

---

### Post by pandam@n on 2009-11-02
I have also the identical problem, but without the RAID, same as zarathustra. I can read to of my four discs. The problem for me is that 9.10 want it to be some errors on the disc, but when running 9.04 live-cd there are not any errors..... have not a clue what to do next...

---

### Post by AndreLeComte on 2009-11-08
I have the same issue although it only occurs with the 2.6.31 kernel. I can boot Ubuntu 9.10 by using the 2.6.28 kernel. Any solution?

---

### Post by AndreLeComte on 2009-11-09
This basically solved the issue for me:
> **arekku said:**
> [Here](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

Replace your nonworking initrd file with a previous version. For you Andre all you need to do is (just in case you are new)

cd /boot
sudo mv initrd.img-2.6.31-14-generic backup
sudo cp initrd.img-2.6.28-16-generic initrd.img-2.6.31-14-generic

---

### Post by jazblue_94 on 2010-01-31
problem occurs when i try to boot my ubuntu 9.10 after i updated it,error message is displayed in the attached images.......

so plz someone help,how to deal with it.....

---


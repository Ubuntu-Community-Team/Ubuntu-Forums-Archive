---
title: "Partition editing"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by balt11t on 2009-10-23
During the installation, everything runs smoothly until I get to the partition editor. There is no option to just resize and install automatically, and when I switch to manual I click on the ntfs drive where my Windows partition is located. When that menu pops up, it doesn't give me an option to change the size of it. Help?

---

### Post by mikewhatever on 2009-10-23
You may need to run a file system check, also known as chkdsk in Windows.
[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)
It's also a good idea to defragment the Windows partition and free as much space as possible.

---

### Post by Mark Phelps on 2009-10-23
First off, are you running Vista or XP?  If Vista, do NOT use the Ubuntu installer to resize your partition.  Doing so runs the risk of corrupting the Vista OS, for which you will then need a Vista DVD in order to run repair utilities.

If you're running XP, that's not a problem. In that case, boot into Ubuntu using the LiveCD, open a terminal and enter "sudo Fdisk -lu" (that's a lowercase L, not a one), and post the results here.

---

### Post by balt11t on 2009-10-23
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325   146496734    73208205    7  HPFS/NTFS
/dev/sda3       146496735   156232124     4867695   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ 


Here's what it says.

---

### Post by balt11t on 2009-10-23
Bump. I really need help with this, it needs to be fixed ASAP.

---

### Post by Mark Phelps on 2009-10-24
> **balt11t said:**
> Bump. I really need help with this, it needs to be fixed ASAP.

I'm presuming that you're NOT running Vista  -- because you didn't bother to answer such a simple question.  If you ARE running Vista, stop what you're doing because you're only going to trash your system and render it unbootable.

So, if you're running XP, download a GPArted LiveCD from distrowatch.com, burn the ISO to a CD, boot from that CD, and use the Partition Editor to do the following:
1) Resize sda2 to make room for Ubuntu
2) Move sda3 to the left to consolidate free space at the right-most side
3) Create an Extended partition to fill the consolidated free space
4) Create a Ext3 partition in the free space, leaving enough space equal to the size of your system memory
5) Create a Linux-swap partition filling the remaining free space in the extended partition.

Reboot using the Ubuntu CD and install using Manual Partitioning, selecting the partitions you just created.

And, in the future, realize that using terms like ASAP is NOT going to get you expedited support!

---

### Post by balt11t on 2009-10-24
I said ASAP because my friend was having similar problems. Thanks though, I'll try that. And no, I'm not running Vista.

---

### Post by balt11t on 2009-10-24
Okay, when I boot Gparted, I select /dev/sda2.  It says the minimum size is 72492 while the max is 71492. When I adjust the New Size (MB), it just flips back to 72492.

---

### Post by balt11t on 2009-10-24
I think I have everything under control.

Thank you for your guys' help

---

### Post by QwUo173Hy on 2009-12-01
Hi balt11t. Could you explain how you resolved your problem?

---


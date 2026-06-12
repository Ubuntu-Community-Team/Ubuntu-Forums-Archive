---
title: "Errors on booting"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by MasterHalo on 2007-06-30
Hello,

I own a lenovo thinkpad T60 (UT063SG) with ubuntu Feisty and have 3 recurring problems that I've been unable to solve, the last of them being pretty bad.
The first two errors appear systematically (spaces may be wrong because I copied the lines by reading them on booting):

[   17.636000] e1000: eth1: e1000_request_irq: Unable to allocate MSI interrupt
Error: -22
[   19.060000] intel_rng: FWH not detected

sometimes the "configuring network interfaces" is very long, if it helps.

My third problem concerns a FAT32 partition in which I put all my personal data. I've done this because I kept a windows XP pro that I sometimes have to use on a 2nd hard disk.  The windows is totally indepedent of GRUB as I took the HDD containing windows out of the laptop when I installed ubuntu. My problem is the following: the message appearing is:


[   23.676000] FAT: bogus number of reserved sectors
mount: wrong fs type, bad option, bad superblock on /dev/sda1
            missing codepage or other error
            In some cases useful info is found in syslog -try
            dmesg ¦ tail or so

The consequence seems to be that the system doesn't mount the partition and that I can only access it with root. I doesn't appear all the time but is more likely to appear when the AC adapter is not connected to the laptop.

It would be really nice if you could help me :)

---

### Post by GeeZor on 2007-06-30
About your problem with mounting the FAT32 disk, look here

[http://ubuntuforums.org/showthread.php?t=267900](http://ubuntuforums.org/showthread.php?t=267900)

Should help you out...

---

### Post by MasterHalo on 2007-06-30
In my case, I haven't change a NTFS in FAT32 and I still have all my datas. The problem is that, when I get the message, (in my first post) the partition is unaccessible for me unless I put the root password(which I guess means that it isn't mounted) and when I don't get the message it works fine. But thank you for answering anyway. Could anyone help me ?

---


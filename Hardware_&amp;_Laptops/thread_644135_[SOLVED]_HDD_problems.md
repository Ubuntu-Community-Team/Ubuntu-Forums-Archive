---
title: "[SOLVED] HDD problems"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by MunkyJunky on 2007-12-18
Hey, firstly Id like to say I'm not at all well versed in Linux, and I've previously only used Fedora Core 5 & 6, and Windows.

I'm currently dual booting Windows XP and Ubuntu 7.10 (Gnome), My system has 3 hard drives, all SATA. The first (a 40G) is split into two 20G partitions, one with windows installed and the other with Ubuntu. The other two are both NTFS drives with all my windows data and apps on them. 

All the windows my Documents stuff is on the second drive, and Id like to be able to get at it off my linux system. Although Ubuntu picks up my 20G Windows partition on the same physical disk, it wont pick up the other two drives (neither in /mnt [I was advised to have a look there] or in the actual device manager in system > Preferences. 

My motherboard is an MSI P965-Neo, which my friend told me does have some problems running Liunux without the latest firmware. Ive updated to the newest firmware, but to no avail. 

So, my question is: How the hell do I get my disks up under Linux? Id like to get my music and such for use, as I'm switching to Linux as my main OS. 

If anyone has any suggestions, or a solution to my problem, I would be very thankful!

---

### Post by nick_h on 2007-12-18
Can you see the drives if you type:
```
sudo fdisk -l
```
?

---

### Post by MunkyJunky on 2007-12-19
No, that just lists the partitions of the 40G HDD, but nothing about any other drives. 

It show this: 
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x030d030c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2472    19856308+   7  HPFS/NTFS
/dev/sda2            2473        4759    18370327+  83  Linux
/dev/sda3            4760        4865      851445    5  Extended
/dev/sda5            4760        4865      851413+  82  Linux swap / Solaris

```

---

### Post by nick_h on 2007-12-19
It looks like a motherboard / driver issue.  A quick search revealed a thread, [here](http://ubuntuforums.org/showthread.php?t=490950) and a possible bug - [#156115](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156115).

Do you get any errors in your dmesg output?  Do you have a PATA optical drive connected?

---

### Post by MunkyJunky on 2007-12-20
I have 2 optical PATA drives connected, and I don't even know what dmsg is! :)

---

### Post by nick_h on 2007-12-20
The reason that I asked about the PATA drives is that in the thread I linked to kyphi said:
> If you use SATA connected drives for both hard drive and optical drive the 965 board will work. If you use IDE connected drives it will not work.
but it was an old post by someone running Dapper.  It still might be worth disconnecting them as a test.

My other suggestion was to look in the error logs.  If you type:
```
dmesg
```
you will see the messages during boot.

The following may be more helpful:
```
dmesg | less
dmesg | grep -i ata
```
which will allow you to scroll easily and to search for lines containing "ata".

You can also run the log viewer from System->Administration->System Log

It would be interesting to see if you have any ATA related log entries.

---

### Post by MunkyJunky on 2007-12-23
I tried disconnecting my IDE drives - no change. 

Ive updated to the Hardy Heron kernel, which has given some mild improvement., Although Theres still nothing about my other 2 drives, I can mount (with R/W) my 20G NTFS Windows partition. Admittedly, thats not what I was going for, I'm still happy Ive got *something* working! 

After trying ```
dmesg | grep -i ata
``` with the Hardy kernel (and my IDE optical drives plugged in) theres still nothing about any of my other drives listed.

---

### Post by nick_h on 2007-12-23
If you can't see any error messages then I don't see that you can do much more except report the bug.

Have a look [here](http://ubuntuforums.org/showthread.php?t=600644) and look at the Debugging Harware Detection section.

---


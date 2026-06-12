---
title: "Continued Hardy crashes : Help post Bug"
date: 2008-05-10
forum: Hardware
---

### Post by acl123 on 2008-05-10
I have had a disastrous time with Hardy. I get fatal crashes that require a hard reset. I want to post a bug about it and then I'm out of here. My computer with Hardy on it is as good as a brick. I don't want to fry my hardware any longer.

Could someone please point me in the right direction to post a bug. I am not sure where this belongs or what causes the issue.
I can sometimes hit Ctrl-Alt-Backspace and drop into a new session, once there, everything is still locked up. If I try and login, it allows me to type my username but it hangs before it even asks for my password. Sometimes I can hit Ctrl-Alt-Delete at this point and reset the computer, but usually not.

Whilst I'm stuck in the non-graphical session, error messages gradually start being displayed. Things like this:
> 
EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal<6>sd 1:0:0:0 [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK, SUGGEST_OK
.
.
.
EXT3-fs error (device sda1): ext3_find_entry: reading directory #590954 offset 0
.
.
.
[124.058330] ata 2.00: revalidation failed (errno=-5)
.
.
.
EXT3=fs error (device sda1):ext3_get_inode_loc: unable to read inode block - inode=8618454, block = 17235984
.
.
.
[224.871822] Buffer I/O Error on device sda1, logical block 46953927
.
.
.
ata 2.00:Status {DRDY}
ata 2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen


I have just finished completely reinstalling Hardy and it is still giving me this trouble.

---

### Post by EXCiD3 on 2008-05-11
[http://launchpad.net/ubuntu](http://launchpad.net/ubuntu) is where bug reports go. It looks like you are having hard drive issues. Have you reformatted the partition recently? Maybe you drive is going bad...

---

### Post by acl123 on 2008-05-11
I had Gutsy and before that Feisty running fine for a year. The problems started immediately after upgrading to Hardy. I tried reformatting the disk and reinstalling Hardy, but the problem continues.
My hard disk is probably going bad now because of all the times I've had to cut the power on the computer to get it to restart, but my hard disk was fine prior to installing Hardy.

---

### Post by EXCiD3 on 2008-05-11
This is an older post but it might be of some help: [http://ubuntuforums.org/showthread.php?t=8106](http://ubuntuforums.org/showthread.php?t=8106)

you should also run fsck on the drive. heres another link on ext3-fs error corruption [http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg04631.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg04631.html)

---

### Post by acl123 on 2008-05-11
Hi, Thanks for the links.
I tried running fsck and couldn't see any errors, except on one partition it finishes straight away with the message *"Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Could this be a zero-length partition?"*. What does this mean.

Here is my fdisk -l output:
> 
/dev/sda1   *   1     2983   23960916   83   Linux
/dev/sda2       2984  30401  220235085  5    Extended
/dev/sda5       29835 30401  4454396    82   Linux swap / Solaris
/dev/sda6       2984  29834  215680594+ 83   Linux


So sda1 and sda6 finish with no problems. sda5 is mounted so I can't run fsck on it. sda2 finishes with the message above.

I'm not really sure what all this means.

---

### Post by 00arthuryu on 2008-05-18
I am having the exact same problem as you

[http://ubuntuforums.org/showthread.php?p=4986754#post4986754](http://ubuntuforums.org/showthread.php?p=4986754#post4986754)

have you filed a bug report of any type?

---

### Post by EXCiD3 on 2008-05-18
> **acl123 said:**
> Hi, Thanks for the links.
I tried running fsck and couldn't see any errors, except on one partition it finishes straight away with the message *"Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Could this be a zero-length partition?"*. What does this mean.

Here is my fdisk -l output:


So sda1 and sda6 finish with no problems. sda5 is mounted so I can't run fsck on it. sda2 finishes with the message above.

I'm not really sure what all this means.

It looks like your 2nd partition is corrupted on your drive. It was unable to read the partition correctly. What did you have on that partition and which drive is Ubuntu 8.04 installed to?

---

### Post by 00arthuryu on 2008-05-18
fdisk -l /dev/sda
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a17b1fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391    b  W95 FAT32
/dev/sda2              14       60801   488279610    f  W95 Ext'd (LBA)
/dev/sda5              14        2563    20482843+   b  W95 FAT32
/dev/sda6            8938       21685   102398278+   b  W95 FAT32
/dev/sda7           21686       34434   102406311    b  W95 FAT32
/dev/sda8           34435       47182   102398278+   b  W95 FAT32
/dev/sda9           47183       60801   109394586    7  HPFS/NTFS
/dev/sda10           2564        7722    41439636   83  Linux
/dev/sda11           7723        8815     8779491   83  Linux
/dev/sda12           8816        8937      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
fdisk -l sdb
```

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x316f316e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       30401   203238315    f  W95 Ext'd (LBA)
/dev/sdb5            5100       10198    40957686    7  HPFS/NTFS
/dev/sdb6           10199       15297    40957686    7  HPFS/NTFS
/dev/sdb7           15298       20396    40957686    7  HPFS/NTFS
/dev/sdb8           20397       25495    40957686    7  HPFS/NTFS
/dev/sdb9           25496       30401    39407413+   7  HPFS/NTFS

```
Intresting, as those partitions should not be NTFS, they are FAT32s on sdb, the only one that should be NTFS is /dev/sdb7 which is agreed on G-parted.

---

### Post by EXCiD3 on 2008-05-18
Do you have an older Ubuntu disk lying around? If you do, I would check and see if fdisk shows the same output on there too.

---

### Post by 00arthuryu on 2008-05-18
Yes on the old CDs it says FAT32 but I don't think that is related to the bug at hand?  maybe its a different one?? lol as my root partition is /dev/sda10 and home is /dev/sda11.
Or could they be related?

---

### Post by EXCiD3 on 2008-05-18
I was just checking to see if there was something wrong with hardy detecting the drive formats on sdb. This is a really odd problem. Has anyone posted a bug on launchpad.net for this yet? There have a been a bunch of people having trouble with their sata controllers and posting about it here on the forums. Unfortunately bugs need to be reported to launchpad as lots of the developers dont read the forums all that often, if at all. I'm not really sure what the problem is, I can just try to help narrow it down. The developers would know the best place to get started on a fix if they have a bug report filed by a few users.

---

### Post by CheShA on 2008-05-18
I have the same problem but for me it only happens when I am running the real time kernel; if I'm running the generic kernel then everything seems fine.

---

### Post by acl123 on 2008-05-18
Hi I posted the original post.
I have posted a bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229159)

I have rolled back to Gutsy now and as expected my computer is fine. So I don't think there is any problems with my hard drive.

I was running Ubuntu Studio, so yes I would have been using the real time kernel.

---

### Post by 00arthuryu on 2008-05-18
oh dear. I am running the generic kernel and i am getting the same problem.
Mine do happen very randomly though, anywhere between just booted up to 12 hours on? this bug is very strange

---


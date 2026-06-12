---
title: "Deleted Hidden files on /home now drive won't mount"
date: 2008-08-11
forum: General Help
---

### Post by naythink on 2008-08-11
Hey, hoping someone can help me recover all my media on my 500gb /home partition?  I tried doing some clean installs of various distro's to try and reset a problem with lirc / LCDd no longer working at all but every one worked exactly the same.  So i figured there must be some config files written on my home partition that the new system was defaulting to.  So rather stupidly i went in and deleted all the hidden files in my home folder that didn't look important, assuming they would just repopulate as needed like preferences in os x, but now i can't mount the drive.

This is what happens:

nathan@MythTV:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I added this to  my /etc/fstab :

# /dev/sdc1
UUID=38c2031e-c930-46c3-a5be-330027bd767e /media/store      jfs       user,fmask=0111,dmask=0000       0        0
But it didn't make much difference except that the error message when trying to mount through nautilus is a lot less specific and just says" Invalid mount option ..."

I ran testdisk but this is the only information i really got from that:

TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

  Linux                    0   1  1 60800 254 61  976768000
superblock 1605632, blocksize=4096

This is all i could find in syslog;
Aug 12 12:51:28 MythTV kernel: [129617.010317] jfs: Unrecognized mount option "fmask=0111"  or missing value
Aug 12 12:51:33 MythTV kernel: [129621.767407] jfs: Unrecognized mount option "fmask=0111"  or missing value
Aug 12 12:51:38 MythTV kernel: [129626.853622] jfs: Unrecognized mount option "fmask=0111"  or missing value

I noticed testdisk had the option to copy contents of the drive, do you have any idea if i could spread the copy over 2 drives?
There is about 350gb of data on there that i don't want to lose, there is two other drives in the system one with 250gb free and the other with 140gb free.


Do you think there's a chance to recover my data?

---

### Post by Mister.Vash on 2008-08-11
Try changing this:
# /dev/sdc1 
UUID=38c2031e-c930-46c3-a5be-330027bd767e /media/store jfs user,fmask=0111,dmask=0000 0 0

To this:
# /dev/sdc1 
UUID=38c2031e-c930-46c3-a5be-330027bd767e /media/store jfs defaults 0 2

And see if it as least mounts with those option?

---

### Post by naythink on 2008-08-12
Ok, Thanks for the help.

I tried your suggestion and there is no difference when I sudo mount -a.

nathan@MythTV:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

But when i try and mount it through Nautilus i now get :

Cannot mount Volume-
You are not priviledged to mount this volume

Any ideas?

---

### Post by lukjad on 2008-08-12
Try this command:

```
gksudo nautilus
```

Then try drilling to the hard drive.

---

### Post by naythink on 2008-08-12
Yeah thanks, I tried that but the hard drive is no longer visible in the sidebar (when I gksudo), and there is nothing in /media/store.  I'm more familiar with os x than linux so i'm not really sure where i should be looking.

---

### Post by nazish on 2008-08-12
hi naythink,
 
can you please post the output of the following command
 
> sudo fdisk -l

---

### Post by naythink on 2008-08-12
Ok, here we go:

```
nathan@MythTV:~$ sudo fdisk -l
[sudo] password for nathan:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          36      289138+  83  Linux
/dev/sda2   *          37        3683    29294527+   7  HPFS/NTFS
/dev/sda3            3684       38913   282984975    5  Extended
/dev/sda5            3684        4716     8297541   82  Linux swap / Solaris
/dev/sda6            4717       38913   274687371   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002eee2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496   83  Linux
/dev/sdb2            3648       24321   166063905    5  Extended
/dev/sdb5            3648       24321   166063873+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e096e09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

---

### Post by nazish on 2008-08-12
fine now let us see what we can do to get your partition working,
 
we will try to mount your /home partition manually from scratch. To do this first let us create a directory
 
> sudo mkdir /media/myhome
then run the following command
> 
[FONT=Courier New]sudo mount /dev/sdc1 -t jfs /media/myhome[/FONT]

 
this should mount your partition if not lets try the other methods.

---

### Post by naythink on 2008-08-12
No luck unfortunately.

```
nathan@MythTV:~$ sudo mkdir /media/myhome
nathan@MythTV:~$ sudo mount /dev/sdc1 -t jfs /media/myhome
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by nazish on 2008-08-12
did you try running the fsck command if not try running it
 > **fsck -t jfs /dev/sdc1**

---

### Post by naythink on 2008-08-12
No, hadn't tried that one, here's what i get.

```
nathan@MythTV:~$ fsck -t jfs /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 8/13/2008 0.11.56

Error: Cannot open device /dev/sdc1

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.

```

---

### Post by naythink on 2008-08-12
Should i try it with "-a" to do an auto repair?

---

### Post by nazish on 2008-08-12
yes also run it with sudo

---

### Post by naythink on 2008-08-12
That worked! Thank you!!!

```
nathan@MythTV:~$ sudo fsck -a -t  jfs /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 8/13/2008 0.18.16
The current device is:  /dev/sdc1
Block size in bytes:  4096
Filesystem size in blocks:  122096000
**Phase 0 - Replay Journal Log
Filesystem is clean.
nathan@MythTV:~$ sudo mount -a
nathan@MythTV:~$ 
```

---

### Post by nazish on 2008-08-12
gr8 then keep njoyin.

---


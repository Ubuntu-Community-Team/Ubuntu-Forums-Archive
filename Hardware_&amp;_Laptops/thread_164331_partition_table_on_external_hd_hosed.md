---
title: "partition table on external hd hosed"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by zaba on 2006-04-22
Hi folks,

I've searched the forums and tried a couple of "system restore" CDs to sole my problem, but to no avail. 

What happened is, I made a backup of hda2 (Ubuntu partition on this machine) as I was about to upgrade to Dapper on this machine (currently on Breezy). After I did this, I did: 

```
cp backup.tar.gz /dev/sdf1
```

to move the backup to my external harddrive. In the process, I have completely lost /dev/sdf1. 

On clicking it through the file browser, I get the following error:

> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail shows:
> 
[4294778.799000] HFS+-fs: unable to find HFS+ superblock
[4294778.811000] VFS: Can't find a HFS filesystem on dev sda1.
[4294778.819000] VFS: Can't find ext3 filesystem on dev sda1.
[4294778.821000] VFS: Can't find an ext2 filesystem on dev sda1.
[4294778.834000] ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
[4294778.870000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4294778.870000] SGI XFS Quota Management subsystem
[4294778.873000] XFS: bad magic number
[4294778.873000] XFS: SB validate failed
[4294778.885000] JFS: nTxBlock = 3911, nTxLock = 31288


(sda1 is the same drive as sdf1 earlier...)

Is there anyway to add a partition table without destroyin all the data that is (or was) on the drive? I have tried the usual suspects (parted, gparted, fixdisktable, etc.) to no avail.

---

### Post by tonyr on 2006-04-22
[QUOTE=zaba]
What happened is, I made a backup of hda2 (Ubuntu partition on this machine) as I was about to upgrade to Dapper on this machine (currently on Breezy). After I did this, I did: 
```
cp backup.tar.gz /dev/sdf1
```
to move the backup to my external harddrive. In the process, I have completely lost /dev/sdf1. 

Is there anyway to add a partition table without destroyin all the data that is (or was) on the drive? I have tried the usual suspects (parted, gparted, fixdisktable, etc.) to no avail.[/QUOTE]

Well, no, but there is some information missing here.  Was there a filesystem already
on the external drive?  Was the external drive mounted?  How was the backup
made?  

The device /dev/sdf1 provides
low-level 'raw' access to the drive partition, so you have overwritten whatever was at the
beginning of the drive, including whatever file system definition (superblock) may
have been there.  Replacing it would likewise destroy part of the data that you
copied.  Usually you have some filesystem on the drive partition (ext3, ext2, hfs, etc,
etc) and it is mounted on a directory, usually in /media.  You copy to the
mounted file system, not the raw device.  There are ways to make 'image'
copies of raw devices, but they are a little more subtle, and I'm not sure
wheter or not that is what you were doing.

If none of this sound familiar,  read man pages for **mkfs** and **mount**.

---

### Post by zaba on 2006-04-22
[QUOTE=tonyr]Well, no, but there is some information missing here.  Was there a filesystem already
on the external drive?  Was the external drive mounted?  How was the backup
made? [/QUOTE]

There was a filesystem on there, but can't remember which. I'm guessing vfat, since my fiancee kept backups of her ms money on sda1 and she could access it from Windows.

I umounted the external drive before doing the backup and then thought I remounted it before cp ing the backup. (That's why the cp went to sdf1... when I ran mount after re-plugging, that is all that showed up.).

the back up was made with this command:

```
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys
```
 
(unrelatedly, I got the code off of one of the ubuntu forums... the excludes didn't seem to work for me.)

[QUOTE=tonyr]The device /dev/sdf1 provides
low-level 'raw' access to the drive partition, so you have overwritten whatever was at the
beginning of the drive, including whatever file system definition (superblock) may
have been there.  Replacing it would likewise destroy part of the data that you
copied.  Usually you have some filesystem on the drive partition (ext3, ext2, hfs, etc,
etc) and it is mounted on a directory, usually in /media.  You copy to the
mounted file system, not the raw device.  There are ways to make 'image'
copies of raw devices, but they are a little more subtle, and I'm not sure
wheter or not that is what you were doing.

If none of this sound familiar,  read man pages for **mkfs** and **mount**.[/QUOTE]


So, it's a given that I shouldn't access sdf* anymore. Thanks for the heads-up on that. If my option is to destroy *some* more data, rather than *all* data (if it is still there), I'll choose some. Will mkfs allow for simply the creation of the superblock? (Yes, I'll read the mans, but if you point me in the right direction, it would be greatly appreciated.)

---

### Post by tonyr on 2006-04-22
> 
So, it's a given that I shouldn't access sdf* anymore. Thanks for the heads-up on that. If my option is to destroy *some* more data, rather than *all* data (if it is still there), I'll choose some. Will mkfs allow for simply the creation of the superblock? (Yes, I'll read the mans, but if you point me in the right direction, it would be greatly appreciated.)

Nope, sorry.  mkfs will virtually wipe the partition.  There is no simple way I know of
to do what you want to do (save part of the data on that external partition as a 
recognizeable file).   A tar file has some internal structural information, so you
kind of have to have the whole thing.  And IIRC you have compressed the file (.gz)
so the situation is further complictated.  Gotta go get my kid a haircut.  Back later.

---

### Post by zaba on 2006-04-22
[QUOTE=tonyr]Nope, sorry.  mkfs will virtually wipe the partition.  There is no simple way I know of
to do what you want to do (save part of the data on that external partition as a 
recognizeable file).   A tar file has some internal structural information, so you
kind of have to have the whole thing.  And IIRC you have compressed the file (.gz)
so the situation is further complictated.  Gotta go get my kid a haircut.  Back later.[/QUOTE]

Thanks for the info, so far. I'm not concerned about saving the backup of hda2 that went to the external drive. I still have a copy of that. What I am concerned about is saving any of the other info that was on the external hard drive before I made the mistake of copying the backup to sdf1... there were pics and music and a lot of other backups on there. Any way to save anything?

---

### Post by tonyr on 2006-04-22
[QUOTE=zaba]Thanks for the info, so far. I'm not concerned about saving the backup of hda2 that went to the external drive. I still have a copy of that. What I am concerned about is saving any of the other info that was on the external hard drive before I made the mistake of copying the backup to sdf1... there were pics and music and a lot of other backups on there. Any way to save anything?[/QUOTE]

There may be, but it falls under the general heading of **Data Recovery**, and that is beyond my
expertise.  There is plenty of  software out there that can examine the partition and recontruct files
from fragments.  There are certainly services that do it.  Both ways cost time and money.  It also depends on
how big the external drive partition is, how big the tar file is, and whether there was more than one
partition on the drive.

---

### Post by nolongerlivecd on 2006-04-23
I've got a solution, though it requires you to boot into Windows. It's something called PC Inspector File Recovery, or something like that. It only recovers your files. Some may be corrupt, though, and I would appreciate it if somebody could also help solve my problem, which is a corrupt hard disk, which I want to reformat entirely, but results in lags, not working in Ubuntu.

---

### Post by kko1 on 2006-05-08
I sympathise with you. In case this is still actual, I'd like to refer you to a tool I came across on this same "Hardware Help" forum. It may be of help in rescuing the data that wasn't overwritten by your backup file.

[SIZE="1"]Based on this thread it seems that the following applies:
- The backup.tar.gz written directly to the device overwrote the beginning of the device / partition.
- From the wikipedia entry for FAT (FAT16 and VFAT, specifically), it seems that the file system table is in that system written near the start of the device / partition - alas, it most probably was completely overwritten, and re-creating the filesystem wouldn't be possible.
- I've read that earlier (when harddrives were in the range of MBs) it was (theoretically) possible to sometimes salvage parts of magnetically recorded data even if it had been overwritten, based on residual magnetic traces. I am unsure whether this still applies (with harddrives in the GB range, i.e. with denser magnetic records). In any case, if it's possible, it is specialist stuff - if really in a fix, you could query a data recovery firm for their services.[/SIZE]

For salvaging what wasn't overwritten, a tool called "foremost" was presented by azz here: [http://www.ubuntuforums.org/showpost.php?p=958549&postcount=10](http://www.ubuntuforums.org/showpost.php?p=958549&postcount=10) . Foremost reads the raw data (directly from the drive or from a copied image) and tries to "recover files based on their headers, footers, and internal data structures". In the thread that azz's message is part of, a person reports using it successfully.

There is an old version in ubuntu repositories, but as azz recommends, I would use the newest version, following azz's link to [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/). He gives directions to compiling it.

Good luck!

Yours, kko.

---

### Post by aysiu on 2006-05-08
dmesg just looks like gibberish to me.

What happens when you plug the drive in and type ```
sudo fdisk -l
```?

---


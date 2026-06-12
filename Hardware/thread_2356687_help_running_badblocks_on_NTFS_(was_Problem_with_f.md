---
title: "help running badblocks on NTFS (was Problem with fsck)"
date: 2017-03-25
forum: Hardware
---

### Post by noenvoli on 2017-03-25
Hi,

I'm using Windows 10. I tried getting help from the tenforums but they said to buy a new laptop (which is true). But I'm just seeing if you guys could find a way to get my hard drive fixed.

When I was in windows, it alerted me that there was a "attribute corruption 123, $bad" and to make a long story short, after I rebooted, Windows 10 just went on an infinite loop showing a BSOD of "Stopcode: Fat file system"

I tried a Windows USB boot but the same error came up (using both windows 10 offficial, and their Windows PE).

I ran their RAM test and after 9 passes, my RAM is fine.

So I tried installing ubuntu into my USB and here i am using the laptop with ubuntu.

Here's what I did:
```

ubuntu@ubuntu:~$ sudo parted /dev/sda 'print'
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  210MB   209MB   primary  ntfs         boot
 2      210MB   977GB   977GB   primary  ntfs
 3      977GB   1000GB  23.3GB  primary  ntfs
 4      1000GB  1000GB  107MB   primary  fat32        lba

ubuntu@ubuntu:~$ sudo unmount /dev/sda3
sudo: unmount: command not found
ubuntu@ubuntu:~$ sudo umount /dev/sda2
ubuntu@ubuntu:~$ sudo parted /dev/sda 'print'
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  210MB   209MB   primary  ntfs         boot
 2      210MB   977GB   977GB   primary  ntfs
 3      977GB   1000GB  23.3GB  primary  ntfs
 4      1000GB  1000GB  107MB   primary  fat32        lba

ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fsck -mcfv /dev/sda2
fsck from util-linux 2.27.1
ubuntu@ubuntu:~$ sudo fsck -mcfv /dev/2
fsck from util-linux 2.27.1
fsck.ext2: invalid option -- 'm'
Usage: fsck.ext2 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ sudo fsck -mcfv /dev/sda2
fsck from util-linux 2.27.1
ubuntu@ubuntu:~$ sudo fsck -mcfv /dev/sda1
fsck from util-linux 2.27.1
ubuntu@ubuntu:~$ sudo fsck -cfv /dev/sda2
fsck from util-linux 2.27.1
ubuntu@ubuntu:~$ sudo fsck -cfv /dev/sda2sudo fsck -mcfv /dev/sda2
fsck from util-linux 2.27.1
fsck.ext2: invalid option -- 'm'
Usage: fsck.ext2 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ sudo fsck -mcfv /dev/sda2
fsck from util-linux 2.27.1
ubuntu@ubuntu:~$ /?
bash: /?: No such file or directory
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 
```

My question is, why does fsck just show "fsck from util-linux 2.27.1" and stop there?

---

### Post by TheFu on 2017-03-26
fsck shouldn't be used on NTFS partitions.  Use Windows disk tools on Windows partitions.

Why are the options -cfv?  That looks like a tar command, not for fsck.  Only one of those options applies to fsck according to the manpage.

```
FSCK(8)                                   System Administration                                  FSCK(8)

NAME
       fsck - check and repair a Linux filesystem

SYNOPSIS
       fsck [-lsAVRTMNP] [-C [fd]] [-t fstype] [filesys...]  [--] [fs-specific-options]

```
Or am I missing something?

---

### Post by noenvoli on 2017-03-26
I got my info from here [http://www.pcrepairmansblog.com/use-linux-boot-disk-to-repair-windows-ntfs-disk-fault-hard-drive-chkdsk-bad-blocks-sectors/](http://www.pcrepairmansblog.com/use-linux-boot-disk-to-repair-windows-ntfs-disk-fault-hard-drive-chkdsk-bad-blocks-sectors/)

he uses -mcfv

---

### Post by TheFu on 2017-03-26
Seems like you really have a **badblocks** question.  That is what he is trying to accomplish using fsck. I've never done that, especially for a Windows partition/disk. I fight lazy bits (bit rot) on Windows by replacing disks every 3 yrs. This action forces all the existing bits to be read and written at least that often, which refreshes the bits.  Doing complete backups periodically will force the read-aspect, but will not refresh the bits with a write unless the drive HW determines a sector relocation is needed. 

I've never seen some of the options that link is suggesting before, but I've only been using Linux for 25 yrs.  For example, ```
sudo parted -l /dev/sda
``` is the normal command.  Do it at the drive level, not at the partition level.  So much I still need to learn.

His fsck command is also odd, since it doesn't specify the type of file system to be repaired. Do Linux distros pre-install the ntfs-3n tools by default?  I don't know. Mine do not, so expecting the normal fsck command to automatically determine the type and run a program that isn't installed just won't work.  That is my current guess for why the command above doesn't seem to do anything - it doesn't recognize NTFS as a valid file system type.

First, **make a clone of the HDD before starting**. That is always step 1 with things like this. I would use **ddrescue** to make the clone. The act of cloning will often force HDDs to re-re-read sectors and force a relocation of any bad areas. The could effectively fix the issue. This assumes there are spare sectors available still. That's where the SMART data comes in. If you can see the SMART data, does the relocated sectors count seem low or high?  I know people who replace a disk if that number goes above 3.  I've had some disks with counts of 7 that have been working perfectly for 5 more years.  I'm religious about backups, so a disk failure is just a minor inconvenience to me.

2nd, using the --force option with any command without being positive *often destroys data*. Linux tools don't have protections from doing incorrect things. Most tools will assume you know what you are asking and will do it, if possible. Sometimes it will attempt to do it even if it isn't possible. That leaves corruption behind and makes any data recovery even worse than before.

YMMV.

BTW, if you could please edit the 1st post and use 'code tags' so the output lines up, that would be VERY helpful to getting others to read this.  I know it would help me. There's an example above to you can see what the 'code' should look like in this post and my prior manpage post.
Not sure if you can change the title or not, but **help running badblocks on NTFS** is what I'd call it. A more descriptive title will help get the type of skilled knowledge wanted.

If you just want to run badblocks and hope it fixes something, try
```
sudo badblocks -vs /dev/sda1
sudo badblocks -vs /dev/sda2
```
This doesn't write anything. 
This doesn't make a list of badblocks to be used later.
Basically, it only exercises the read parts of the disk. On a normally working disk, this won't do any harm.  On a disk that is failing due to surface defects, it can make the drive head fail. Whether you want to run it or not is completely up to you.

Step 1 - make a clone of the HDD before starting. Did I mention that?

---

### Post by noenvoli on 2017-03-26
> **TheFu said:**
> Seems like you really have a **badblocks** question.  That is what he is trying to accomplish using fsck. I've never done that, especially for a Windows partition/disk. I fight lazy bits (bit rot) on Windows by replacing disks every 3 yrs. This action forces all the existing bits to be read and written at least that often, which refreshes the bits.  Doing complete backups periodically will force the read-aspect, but will not refresh the bits with a write unless the drive HW determines a sector relocation is needed. 

I've never seen some of the options that link is suggesting before, but I've only been using Linux for 25 yrs.  For example, ```
sudo parted -l /dev/sda
``` is the normal command.  Do it at the drive level, not at the partition level.  So much I still need to learn.

His fsck command is also odd, since it doesn't specify the type of file system to be repaired. Do Linux distros pre-install the ntfs-3n tools by default?  I don't know. Mine do not, so expecting the normal fsck command to automatically determine the type and run a program that isn't installed just won't work.  That is my current guess for why the command above doesn't seem to do anything - it doesn't recognize NTFS as a valid file system type.

First, **make a clone of the HDD before starting**. That is always step 1 with things like this. I would use **ddrescue** to make the clone. The act of cloning will often force HDDs to re-re-read sectors and force a relocation of any bad areas. The could effectively fix the issue. This assumes there are spare sectors available still. That's where the SMART data comes in. If you can see the SMART data, does the relocated sectors count seem low or high?  I know people who replace a disk if that number goes above 3.  I've had some disks with counts of 7 that have been working perfectly for 5 more years.  I'm religious about backups, so a disk failure is just a minor inconvenience to me.

2nd, using the --force option with any command without being positive *often destroys data*. Linux tools don't have protections from doing incorrect things. Most tools will assume you know what you are asking and will do it, if possible. Sometimes it will attempt to do it even if it isn't possible. That leaves corruption behind and makes any data recovery even worse than before.

YMMV.

BTW, if you could please edit the 1st post and use 'code tags' so the output lines up, that would be VERY helpful to getting others to read this.  I know it would help me. There's an example above to you can see what the 'code' should look like in this post and my prior manpage post.
Not sure if you can change the title or not, but **help running badblocks on NTFS** is what I'd call it. A more descriptive title will help get the type of skilled knowledge wanted.

If you just want to run badblocks and hope it fixes something, try
```
sudo badblocks -vs /dev/sda1
sudo badblocks -vs /dev/sda2
```
This doesn't write anything. 
This doesn't make a list of badblocks to be used later.
Basically, it only exercises the read parts of the disk. On a normally working disk, this won't do any harm.  On a disk that is failing due to surface defects, it can make the drive head fail. Whether you want to run it or not is completely up to you.

Step 1 - make a clone of the HDD before starting. Did I mention that?

Hi TheFu,

Thanks so much for your very detailed reply. I can tell you put so much time and effort. I think you're right that fsck won't work on NTSF.

It dawned on me that I could probably install Wine on Ubuntu (in the usb) and then run a window's HDD checking tool. But I couldn't install Wine. . . too many packages missing and errors. I tried looking for a ubuntu ISO with wine installed already. No luck.

Instead i came across Gnome Disks, and here's what it told me about my HDD:

[ATTACH=CONFIG]274313[/ATTACH]

I think trying to fix the HDD is a vain effort.

I really wish I knew that when the error popped up from Windows, that it was the last time I'd be able to use my laptop again. . . I would've done so many things differently. :(

What do you think?

---

### Post by TheFu on 2017-03-26
I think you should clone the disk and figure out what to do next based on how that works or doesn't work.  I would also suggest getting "*backup religion*" so that issues like this are a minor inconvenience next time.

WINE is for high-level applications, not low-level HW access.

---

### Post by sp40140 on 2017-03-27
One more thing. At the worst, you have bad hard drive. You can just buy a new one, unless you want a new laptop. 
Good luck with troubleshooting.

---


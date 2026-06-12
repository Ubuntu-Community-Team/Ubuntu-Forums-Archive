---
title: "Hard Drive / GRUB Problem After Hard Shutdown"
date: 2023-04-10
forum: Hardware
---

### Post by georgeb53 on 2023-04-10
Hello There, thanks for any Help in Advance any suggestions will be apreciated since am a Newb to Linux.
and i am not sure if it's a software or a hardware Problem am stuck with:


1. general discription of the Problem:
a few days ago after waking my Ubuntu 22.04 from suspend and entering the user Password it froze for like 10 Minutes so i did a Hard Shut down IE: Pressed the Power Button for 10 sec, to restart it and it Landed in The GRUB showing me an empty Command Line and after entering ls command i got the Following :
grub [COLOR=#202124][FONT=&quot]> ls

[/FONT][/COLOR](proc) (memdisk) (hd0) (hd0,GPT2) (hd0,GPT1) error: failure reading sectore 0x1000800 from 'hd0'.

and when i tried rebooting or going into the BIOS to reset setting to default didn't do anything, so i went to the BIOS and did an Linovo Diagnostic test and the Hard Drive Self Test Failed and all Others have Passed and the error Code for the NMESel Test Fail is : UHD0400004000 - UJOYHD and the Final Result Code For all the tests is: 41PVNQS39 - D4F3K3 


after that i installed an ubuntu Live Version and booted the Laptop from it and it works but it doesn't see the Hard Drive in the File Explorer and in the Termianl after entering sudo fdisk -l     i see two Partitons of my 512GB SSD M2. WD:

/dev/nvme0nn1 512 KB ( EFII ) i could mount it later
/dev/nvme0nn1 490 GB ( linux) i Couldn't be mounted

Then i Tried  Boot Repair and it didn't show me an option to repair just the the option to paste the the log : [https://paste.ubuntu.com/p/qVzFbDhdBb/](https://paste.ubuntu.com/p/qVzFbDhdBb/)

Gparted is showing the tow Partions withtout the options to check or  Attempt Data Recovery, can't select them (grayed out).

P.S : lastly and i don't know if this is important or significant in anyway but the reason i think that it could be a software problem is that the day before it crashed an update poped up and installed it and i didn't do either the Live Patch or the System Restart after the update and just kinda forgot about it and put it in suspend and the next day the crash Happend first thing when trying to wake the sytem and it froze and when i did the Hard shut down i may have corrupted some Files or something that didn't install properly and were still in the RAM and not saved to the Hard Drive after i Updated the system and didn't restart.

thanks for the Help. George

---

### Post by oldfred on 2023-04-10
You show UEFI Secure Boot on? Was your original install with it on?
Resetting UEFI probably turned it on, which is ok if that is how you installed. But if you installed with it off, you need to turn it off again.

Hard shutdown when system is in middle of something often corrupts file system.
Boot-Repair only fixes grub issues, you may need to run fsck or e2fsck on all the ext4 partitions.

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

To run fsck partition must be unmounted:
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters. If sda1 is the ext4 partition:
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

If SSD is NVMe then device is /dev/nvme0n1p1 or p2.

See also 
man e2fsck
or 
man fsck

---

### Post by georgeb53 on 2023-04-10
Hello @Oldfred thanks for your Help, 


about the [COLOR=#000000] UEFI Secure Boot ,  i didn't install the OS and the device is a rental From a Bootcamp where i am Student and i has another User On it (am not the Admin user on the device) so[/COLOR][COLOR=#000000] i have no idea if it was on or if i turned it on.
[/COLOR]
i ran sudo swapoff --a then i ran the first command [COLOR=#000000]sudo e2fsck -C0 -p -f -v /dev/nvme0n1 and got the following:

e2fsck Bad magic number in super-block while trzing to open [/COLOR][COLOR=#000000] /dev/nvme0n1
[/COLOR][COLOR=#000000] /dev/nvme0n1:
the superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem if the device is valid and it really contains an [/COLOR][COLOR=#000000]ext2/ext3/ext4 filesystem (and not swap or or ufs or something else), then  the superblock is corrupt, and you might try runnig e2fsck with an alternate superblock:

 [/COLOR][COLOR=#000000]   e2fsck -b 8193 device[/COLOR]

[COLOR=#000000]or[/COLOR]

[COLOR=#000000]   e2fsck -b 32768 device[/COLOR]

[COLOR=#000000]Found a gpt partition table in [/COLOR][COLOR=#000000][COLOR=#000000]/dev/nvme0n1[/COLOR][/COLOR]


[COLOR=#000000]should i run one of those or run the second command ?[/COLOR]

[COLOR=#000000]thanks for the help[/COLOR]

---

### Post by georgeb53 on 2023-04-10
e2fsck -b 8193 device

or 

e2fsck -b 32768 device


should i run one of those or run the second command ?

thanks for the help

---

### Post by georgeb53 on 2023-04-10
sorry i forgot the last line :

Found a gpt partition table in [COLOR=#000000]/dev/nvme0n1[/COLOR]

---

### Post by oldfred on 2023-04-10
Is p1 the FAT32 ESP?
You did not post this to see which partition(s) are ext4.
sudo parted -l

fsck or e2fsck is only for ext family of formats.

If p1 is FAT32 then dosfsck
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/nvme0n1p1
The -a seems to help in clearing dirty bit

---

### Post by georgeb53 on 2023-04-11
Hello Olfred,

accordin to sudo parted-l:

the P1 is fat32, Name: EFI System Partition, Flags: boot, esp, 

i ran the command above it gave me he following: 

dsck.fat 4.2 (2221-01-31)
[COLOR=#000000] /dev/nvme0n1p1: 15 files, 2509/130811 clusters

what should i do next ?

Ps it's still booting to GRUB after this.

Thanks,[/COLOR]

---

### Post by oldfred on 2023-04-11
Please post entire command & use code tags if more than a few lines.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Did you run e2fsck on p2?

---

### Post by georgeb53 on 2023-04-11
[COLOR=#000000]i ran [/COLOR][COLOR=#000000] [/COLOR]**```
 **[COLOR=#000000]sudo swapoff --a [/COLOR][COLOR=#000000] [/COLOR]**
``` **[COLOR=#000000]then i ran the first command [/COLOR][COLOR=#000000] [/COLOR]**```
 **[COLOR=#000000][COLOR=#000000]sudo e2fsck -C0 -p -f -v /dev/nvme0n1p2 [/COLOR][/COLOR][COLOR=#000000] [/COLOR]**
``` **[COLOR=#000000][COLOR=#000000]and got the following:

[/COLOR][/COLOR]**```
**[COLOR=#000000][COLOR=#000000]
e2fsck input/output error while trying to open [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]/dev/nvme0n1p2
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]/dev/nvme0n1p2:
the superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem if the device is valid and it really contains an [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]ext2/ext3/ext4 filesystem (and not swap or or ufs or something else), then the superblock is corrupt, and you might try runnig e2fsck with an alternate superblock:

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]    e2fsck -b 8193 (device)[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]or[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]    e2fsck -b 32768 (device)[/COLOR][/COLOR]

**
```**

---

### Post by georgeb53 on 2023-04-11
i didn't run 
```
[COLOR=#000000]sudo e2fsck -f -y -v /dev/sda1[/COLOR]

```

---

### Post by TheFu on 2023-04-11
If this is a computer owned by a boot camp, I'd call them and have them swap it out.  That's why you pay them. It isn't your problem.

---

### Post by georgeb53 on 2023-04-11
Thanks for the reply TheFu, already did but sadly i didn't do any backup (my bad) and i will lose everthing i have been working on for 14 months, that's why am despreat for a fix or atleast to be able to read the Drive if not boot from it to recover the Data.

---

### Post by TheFu on 2023-04-11
> **georgeb53 said:**
> Thanks for the reply TheFu, already did but sadly i didn't do any backup (my bad) and i will lose everthing i have been working on for 14 months, that's why am despreat for a fix or atleast to be able to read the Drive if not boot from it to recover the Data.

No backups?  Didn't they teach you to use a DVCS and haven't you been pushing your code to gitlab or at least an external HDD with a Linux file system?

---

### Post by tea for one on 2023-04-11
Have a look at this info about superblocks
[https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

I know that the site is dated August 2008 but I cannot find anything more recent.

Your disk is nvme0n1 and therefore you have to replace sda with nvme0n1 in the terminal instructions.
sda2 becomes nvme0n1p2.

---

### Post by georgeb53 on 2023-04-11
[COLOR=#111111][FONT=Menlo]thanks for the reply  tea for one ,

i ran:
[/FONT][/COLOR][COLOR=#000000]#[/COLOR][COLOR=#111111][FONT=Menlo]
dumpe2fs /dev/[/FONT][/COLOR][COLOR=#000000]nvme0n1p2[/COLOR][COLOR=#111111][FONT=Menlo] | grep superblock
[/FONT][/COLOR][COLOR=#000000]#
and i got back 
[/COLOR][COLOR=#000000]#
dumpe2fs 1.46.5 (30- Dec-2021)
[/COLOR][COLOR=#000000]dumpe2fs: permission deneid While trying to open /dev/nvme0n1p2
[/COLOR][COLOR=#000000]couldn't find valid filesystem superblock.
[/COLOR][COLOR=#000000]#[/COLOR]

---

### Post by georgeb53 on 2023-04-11
@The Fu,

i can recover about 75 % of the local repos from my github but i will still lose a lot of unpushed Projects + Documents, unscincronized Bookmarks .... etc, it's gonna set me back

---

### Post by oldfred on 2023-04-11
Permission denied usually means you did not use sudo.
Some instructions on Internet are for those systems that use admin or root accounts and then sudo not needed on each command.

sudo dumpe2fs

---

### Post by georgeb53 on 2023-04-11
[COLOR=#111111][FONT=Menlo]forgot about sudo but still the same when i ran: it with sudo as before
[/FONT][/COLOR][COLOR=#000000][COLOR=#000000]#[/COLOR][/COLOR][COLOR=#111111][FONT=Menlo]
sudo dumpe2fs /dev/[/FONT][/COLOR][COLOR=#000000][COLOR=#000000]nvme0n1p2[/COLOR][/COLOR][COLOR=#111111][FONT=Menlo] | grep superblock
[/FONT][/COLOR][COLOR=#000000][COLOR=#000000]#
and i got back
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]#
dumpe2fs 1.46.5 (30- Dec-2021)
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]dumpe2fs:Input/output While trying to open /dev/nvme0n1p2
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]couldn't find valid filesystem superblock.
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]#[/COLOR][/COLOR]

---

### Post by oldfred on 2023-04-11
Have you tried testdisk or photorec.
I have used photorec, it takes a long time & needs another drive to copy data into. And does not recover full filename.
Testdisk has deeper search and may find files, it found immediately copy to another drive.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

I have never used this of course change the example /dev/sdd2 to your ext4 partition:
man ext4magic
sudo ext4magic /dev/sdd2 -a $(date -d "-120hours" +%s)
ext4magic can extract the information from the journal and restore files in an
entire directory tree, if the information in the journal are sufficient.

---

### Post by tea for one on 2023-04-11
> **georgeb53 said:**
> Gparted is showing the tow Partions withtout the options to check or  Attempt Data Recovery, can't select them (grayed out).
Shot in the dark, but can you try, one command at a time (via a live session):-
```
sudo umount /dev/nvme0n1p1
```
```
sudo umount /dev/nvme0n1p2
```
```
sudo dumpe2fs /dev/nvme0n1p2 | grep superblock
```

---

### Post by TheFu on 2023-04-11
> **georgeb53 said:**
> @The Fu,

i can recover about 75 % of the local repos from my github but i will still lose a lot of unpushed Projects + Documents, unscincronized Bookmarks .... etc, it's gonna set me back

Hope you've learned.  If you keep everything in your HOME, 2 commands will backup that and retain 90 days of versioned backups for about 1.3x the source space.  So, if your source is 10GB, then the backup storage will be about 13GB while holding 90days of versioned backups.  Seems like a bargain to me.  Just ensure that the target storage for the backups is different media and has a native Linux file system - something like ext4, zfs, f2fs. Any of those would be fine.  

This would backup everything in the HOME directory for all users on the system with HOME directories under /home/.  If you place HOME directories elsewhere, add those to the --include list for the backup tool you use.

---

### Post by georgeb53 on 2023-04-12
[COLOR=#000000]*@The Fu,*[/COLOR][COLOR=#000000]

those two commands you mean that @olfred posted?
[/COLOR][COLOR=#000000]#[/COLOR][COLOR=#000000]
man ext4magic[/COLOR]
[COLOR=#000000]sudo ext4magic /dev/sdd2 -a $(date -d "-120hours" +%s)
[/COLOR][COLOR=#000000]#[/COLOR]

---

### Post by TheFu on 2023-04-12
No.  I'm talking about doing backups, not recovering your data.
[Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)

I seldom need to know anything about data recovery, because I have automatic, daily, versioned, backups.  When I do, I use ddrescue to get all data possible off the dying storage onto new storage, then work to recover leaving the original storage alone.

**ext4magic** looks interesting. I've never heard of it nor used it.

---


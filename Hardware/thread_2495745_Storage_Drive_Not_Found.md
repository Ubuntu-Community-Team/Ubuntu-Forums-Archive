---
title: "Storage Drive Not Found"
date: 2024-02-29
forum: Hardware
---

### Post by tomreid10 on 2024-02-29
Hi all, am returning to Ubuntu after a few years away, as I’m trying to keep a few PCs and laptops running after Apple and Microsoft are ending support for relevant operating systems.  
 
 
 Have encountered an issue with a PC this morning.  
 
 
 When it was a Windows 10 machine it was set up with 2 internal drives. An SSD which was the boot drive and a 2TB mechanical storage drive.  
 
 
 It seemed to work just fine set up that way when I loaded Ubuntu 22.04.4 LTS around 3 days ago.  
 
 
 Today when I try to access the storage drive I’m getting a “Unable to Access Location” error.  
 
 
 When I check the storage drive in the “Disks” app it looks fine.
 
 
 When I tried to run the fix outlined here:  [https://askubuntu.com/questions/696043/external-harddisk-detected-but-not-mounting](https://askubuntu.com/questions/696043/external-harddisk-detected-but-not-mounting) when I ran the terminal commands I eventually hit a “disk is corrupt” error.  
 
 
 Screenshots  in the attached file.  
 
 
 Thanks

---

### Post by TheFu on 2024-02-29
I don't trust *Gnome Disks*.  It is dumbed down too much.

Use **gparted** instead.  It is easier, but only for partitioning.  It doesn't mount or check SMART data.

For mounting, use the /etc/fstab text configuration file.  Admins should be the only people mounting storage.  For sometimes mounted storage, you might want to use **autofs**. That's up to you.

To run a SMART test, install smartmontools package, then run a **short** test on the whole drive you are worried about.  For an NVMe SSD, SMART won't show much. For SATA SSDs, it will match what HDDs have.  The **smartctl -t short** command needs at least 1 option, but if you have a non-standard controller or it is going through a USB connection, it is more likely to need the controller card specified.  Of my 20 HDDs, only 4 need this, so it isn't THAT common, but it is a flexible aspect of the smartmontools package team.

Anyway, smartctl will provide an estimated time to completion.  For SSDs it will be 1 or 2 minutes. For HDDs, it might be 2-10 minutes for the short test.  Long tests, which I run monthly, can require 24 hrs for large disks.
```
$ sudo smartctl -t short /dev/sda
```

When the tests complete, then you can request a report from **smartctl**.
```
$ sudo smartctl -a /dev/sda | less
```
If you need more specifics about smartctl, there are a few threads here about it.

That's one possible way to figure out if the hardware is showing problems.  Look at the raw data field in the far right.  You want **0** for all of them, unless they are non-error/non-relocated counts or power on hours.

If a file system is corrupt, in Unix there's something called **fsck** - file system check.  The file system cannot be mounted when the check is running, so if it is part of the OS storage that is corrupt, you'll need to boot into rescue mode (under the Advanced Grub boot menu) or boot into a *Try Ubuntu* environment that all Desktop ISO flash drives/install drives allow.  From the running **Try Ubuntu** OS, open a terminal and run fsck against all the native Linux file systems. It doesn't work for NTFS, exFAT, FAT32 or other foreign file systems.  It doesn't work for ZFS or BTRFS either, to my knowledge.  You'll need to understand partition device names. DO NOT RUN FSCK on the whole disk device. That could be bad, though I hope fsck would prevent it, since it is extremely common.

You can google for how-to use **fsck** if you need more help.

fsck and smartctl work the same regardless of which flavor of Linux you run.  Most Linux systems will have the same device naming standards too. I've never seen any that varied, but I haven't seen everything.

A handy book, free, no-hassle download to help you with working at the CLI/shell: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)   Good to have a copy local.

---

### Post by yancek on 2024-02-29
>  When it was a Windows 10 machine

The above comment from your original implies that you no longer have windows.  If that is the case, why do you have an ntfs filesystem on the external drive?  Do you share data with windows users?  What happens when you manually mount the partition on the external drive?  How did you try to access the partition?  Was it through a GUI interface?  How many drives do you have attached?  The information you posted shows the external drive you are referring to as sdf1.

---

### Post by TheFu on 2024-02-29
NTFS isn't needed to share files with Windows users over the network.  
NTFS is only needed if you dual boot.

---

### Post by tomreid10 on 2024-03-02
Thanks all - I'd missed the fact that the storage drive was still formatted to NTFS. I re-formatted to EXT 4 and all seems fine now.

---

### Post by TheFu on 2024-03-02
> **tomreid10 said:**
> Thanks all - I'd missed the fact that the storage drive was still formatted to NTFS. I re-formatted to EXT 4 and all seems fine now.

Please help the community be more efficient and use the _Thread Tools button_ to mark this thread **SOLVED**. Don't waste people's time, if you can avoid it.   People looking for answers, search on "SOLVED" threads.  People looking to help with answers/ideas won't click on SOLVED links, saving them time too.

---


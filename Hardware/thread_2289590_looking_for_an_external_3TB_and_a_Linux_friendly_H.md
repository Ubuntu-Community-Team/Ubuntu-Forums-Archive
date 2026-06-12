---
title: "looking for an external 3TB and a Linux friendly HD"
date: 2015-08-05
forum: Hardware
---

### Post by daniel294 on 2015-08-05
I'm currently looking for an external 3TB HD for backups. I found this one – WDBFJK0030HBK
But it seems it is not compatible with Linux. Has anyone tried this HD? Are there any 3TB external drives that actually work with Linux (no dumb preinstalled software and pre-partitioning)?

---

### Post by TheFu on 2015-08-05
I've never heard of any HDD that wasn't compatible with Linux.
Just ignore the prior format and any software provided. Use it like any other HDD.

Be careful of 3TB Seagates. They have terrible failure rates ... like 40%.

---

### Post by daniel294 on 2015-08-05
Well, I read some more and it looks like the problem is with the GPT instead of the MBR. There is nothing you can do about it and so there is no way to install Linux on this drive.
I don't need to install any OS on the drive but I do need it for backup storage attached to my Linux (Ubuntu) server.
I also found (actually on this very forum) this:
[http://ubuntuforums.org/showthread.php?t=2208483](http://ubuntuforums.org/showthread.php?t=2208483)
[http://ubuntuforums.org/showthread.php?t=1506476&p=9441162&viewfull=1#post9441162](http://ubuntuforums.org/showthread.php?t=1506476&p=9441162&viewfull=1#post9441162)
What do you think, should I take a chance and get one of these HD?

---

### Post by oldfred on 2015-08-05
Many users have installed Linux on gpt partitioned drives. And drives over 3TiB need gpt partitioning.
If system is only BIOS, you need a bios_grub partition. If system is UEFI you need an ESP- efi system partition. I actually have put both on all new drives even small one's like my flash drives as then I had BIOS, but had planned & now have an UEFI based system.

What creates problems is some systems create a faux MBR system to work with XP as XP is the only version of Windows that does not work with gpt. Or they use non-standard sector sizes. Best to partition with gparted or gdisk which is the fdisk for gpt drives.
 Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.


Windows only boots from gpt with UEFI but can use gpt for data. And if external drive you cannot install Windows anyway.


Many users just by a standard 3TB drive and put into a USB caddy if not internal drive. But some older caddies do not work with larger drives so if you go that route make sure it works with larger drives. Some caddys also do not work with USB3 ports. Best to make sure caddy is compatible with everything even if only for future use.

---

### Post by TheFu on 2015-08-05
Uh - I have multiple GPT formated drives here. - I prefer it over MBR and even on smaller disks use GPT. They all work with Linux.  I boot off a 4TB drive. It is on a BIOS boot and it is GPT formated.

These drives have been used both internally and over USB2 and now USB3 connections.  The trick is not to use old versions of fdisk, sfdisk or cfdisk. Use **parted** and **gparted** for partitioning and things will be handled correctly.

The only issue with GPT, as oldfred says above, is with MS-Windows. Then you just have to know MSFTs rules.  Under Linux, those rules do not matter.

---

### Post by weatherman2 on 2015-08-05
> **daniel294 said:**
> Well, I read some more and it looks like the problem is with the GPT instead of the MBR. There is nothing you can do about it and so there is no way to install Linux on this drive.
I don't need to install any OS on the drive but I do need it for backup storage attached to my Linux (Ubuntu) server.

Right - big difference there.  Using it for external storage is different from needing to boot from it.

Like The Fu, I've never encountered an external HD that didn't work with Ubuntu.  Only if the Ubuntu server is running on really old hardware where the 2TB barrier/GPT is an issue would I worry at all.  At worst, you buy it and you can only use 2.1TB maximum partition sizes - but I doubt you'll have any issues with it.

---


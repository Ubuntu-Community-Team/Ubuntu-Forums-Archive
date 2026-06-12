---
title: "Is it a good idea to keep using MBR on rather small drives ?"
date: 2020-10-02
forum: Hardware
---

### Post by hk42 on 2020-10-02
The idea is to be able to use them on old devices or with old OS.

---

### Post by sudodus on 2020-10-02
There is nothing wrong with booting in the old BIOS mode using grub-pc and a master boot record at the head end of the drive. You could even make a portable drive bootable *both* in BIOS mode and the newer UEFI mode. See this link:

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Maybe (probably?) in the future, computers will no longer boot in BIOS mode ...

---

### Post by oldfred on 2020-10-02
How old is old.
Some consider a 5 year old system as old. Others a 15 year old system.

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012. But users can still install Windows 10 in BIOS but only with MBR partitioning.

I had used MBR with my old (2006) XP & Ubuntu laptop (mostly retired but now only 20.04), but converted to gpt when I retired XP and updated to newer LTS version. 
My newer BIOS only desktops I started to convert to gpt in 2010. Windows XP required MBR, but I installed Ubuntu with gpt on separate drive. And from then on, all new or repartitioned drives were gpt.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

About only reason for MBR is if system over 10 years old or you have to have Windows in BIOS boot mode on that drive.

---

### Post by sudodus on 2020-10-02
We have to sort out what we mean by MBR.

- I mean master boot record, that can be created by grub-pc or syslinux to boot in BIOS mode.

- Oldfred means the old style (legacy) partition table, that I call 'MSDOS partition table'.

So we have been talking about different things. (Need I add that oldfred and I have different native languages?)

**What do *you* mean by MBR, *hk42*?**

---

### Post by oldfred on 2020-10-02
The MBR is actually only the first 512 bytes of a drive that is partitioned with the msdos/dos partition table that was started with IBM's PC in early 1980's. Part of MBR is for boot code and part for list of the standard 4 primary partitions.

And even gpt has a protective MBR with one partition table entry, just so old partition tools will see drive as partitioned and not automatically try to partition it.

But the msdos partition table is often called MBR.
[https://en.wikipedia.org/wiki/Partition_table](https://en.wikipedia.org/wiki/Partition_table)

---

### Post by hk42 on 2020-10-03
Thanks for the answers and the links.
May be MBR is not the right term.Partition mode may be better.
My idea is that for example an USB drive can be used on a Wxp PC,on a TV set top Box
running Linux or Android,or on a brand new PC with Linux or W10.
In case it goes wrong you may have ,and be used to ,an old repair tool.
In fact the links provided answered my question .

---


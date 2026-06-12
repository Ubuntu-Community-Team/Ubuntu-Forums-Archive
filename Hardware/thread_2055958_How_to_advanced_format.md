---
title: "How to advanced format?"
date: 2012-09-10
forum: Hardware
---

### Post by Ikmal2129 on 2012-09-10
hi,
I just bought a new hard disk digital wastern model WD3200BPVT that support advanced format, and now I do not know how to setting the lubuntu to be 4KB per sector and get alignment to get the best performance, can anyone help me? btw i'm already google it and can't understand :(

---

### Post by TheFu on 2012-09-10
If you use Gparted, whatever you do should be fine.  If you are using current versions of disk tools 12.04+, and perhaps older, the alignment is handled correctly.  You might want to use GPT (not MBR) for the partition table, but if you do, I've read that a separate /boot partition is required.

Some reading:
* [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
* [http://ubuntuforums.org/showthread.php?t=1735818](http://ubuntuforums.org/showthread.php?t=1735818) 

My understanding is that we only need to be careful if we are trying to clone data or entire partitions between 4k and 512b sector HDDs.  Don't think that works at the byte level.  However, if you use something like rsync, there won't be any issues.

---

### Post by Ikmal2129 on 2012-09-12
If i just want 1 partion, can i install ubuntu with just "Erase disk and install ubuntu" option?

like this picture [http://howtoubuntu.org/wp-content/uploads/2012/04/3-Choose.png](http://howtoubuntu.org/wp-content/uploads/2012/04/3-Choose.png)

---

### Post by TheFu on 2012-09-12
> **Ikmal2129 said:**
> If i just want 1 partion, can i install ubuntu with just "Erase disk and install ubuntu" option?

like this picture [http://howtoubuntu.org/wp-content/uploads/2012/04/3-Choose.png](http://howtoubuntu.org/wp-content/uploads/2012/04/3-Choose.png)

**I don't know.**  I've never, ever, used that.  Partitioning is the most important aspect to setting up a Linux system that I never want to trust any installer to do what I want.

If this is a new, big, HDD and going to be used for Windows7 or later AND Linux, then I'd
* Use GPT partitioning, not MBR.  GPT doesn't have the dumb physical/logical partition issues and keeps 2 copies of the boot records. It supports 128 partitions.  
* Create 4 partitions:
** /boot 500mb (just for kernels, ext2)
** / 20GB (OS and Apps, ext4)
** swap - 1-4GB depending on my RAM. More than 4GB in swap is a was
** /home - (ext4) Whatever is remaining on the disk (?100G+?) that I can support with a backup disk.  If I can't backup the storage, I don't want it available and leave it empty.  Expanding partitions later is easy in Linux.  On my main desktop, /home is about 5GB. I keep large files elsewhere.

I hope that helps. Use the "do something else" option and manually setup the partitions that way.  By keeping HOME separate, OS updates will be easier in the future.  If you ever need to use Windows-whatever later, GPT is supported.  

WinXP does not support GPT partitioning, so something else will be necessary if that is your need from a dual boot solution.

---

### Post by Ikmal2129 on 2012-09-12
> **TheFu said:**
> **I don't know.**  I've never, ever, used that.  Partitioning is the most important aspect to setting up a Linux system that I never want to trust any installer to do what I want.

If this is a new, big, HDD and going to be used for Windows7 or later AND Linux, then I'd
* Use GPT partitioning, not MBR.  GPT doesn't have the dumb physical/logical partition issues and keeps 2 copies of the boot records. It supports 128 partitions.  
* Create 4 partitions:
** /boot 500mb (just for kernels, ext2)
** / 20GB (OS and Apps, ext4)
** swap - 1-4GB depending on my RAM. More than 4GB in swap is a was
** /home - (ext4) Whatever is remaining on the disk (?100G+?) that I can support with a backup disk.  If I can't backup the storage, I don't want it available and leave it empty.  Expanding partitions later is easy in Linux.  On my main desktop, /home is about 5GB. I keep large files elsewhere.

I hope that helps. Use the "do something else" option and manually setup the partitions that way.  By keeping HOME separate, OS updates will be easier in the future.  If you ever need to use Windows-whatever later, GPT is supported.  

WinXP does not support GPT partitioning, so something else will be necessary if that is your need from a dual boot solution.

Woah, very nice instruction, i'm appreciate,
thanks, i will try later :p:D

---

### Post by oldfred on 2012-09-12
+1 on the suggestions by        TheFu.

With gpt you also need a 1MB partition with the bios_grub flag. Use the right click set flags to choose bios_grub. Without that small partition grub2 does not install corrrectly. The installer may add it now if there is space, not sure.

You generally do not want one very large system partition or root partition. Much better to have a smaller system partition. We have seen with some hardware, issues booting from very large system partitions.

If you are ever thinking of Windows on this drive do not use gpt. I changed to gpt on two drives so far. Kept XP in a old MBR drive and they all worked ok together. But now I do not boot the XP drive as I had to change BIOS to AHCI mode for my SSD. You may also need AHCI in BIOS for a 4K drive.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by Ikmal2129 on 2012-09-17
Thank you guys , you all are rocks :guitar:

---


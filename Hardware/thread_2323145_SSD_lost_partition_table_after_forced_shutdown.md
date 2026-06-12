---
title: "SSD lost partition table after forced shutdown"
date: 2016-05-03
forum: Hardware
---

### Post by Matyy on 2016-05-03
Hey,

my notebook was hanging and I used the power button to forcefully shut it down. Now, the partitions are gone. My main partition was using EXT4, Ubuntu 15.10 installation defaults.

I had this before. I should have been more patient, obviously it was still working on something....

So the last time I recovered the partition table and than used fsck. And some stuff came back, other stuff did not. Mostly because I had my home encrypted. So I got my system files back but not my data XD

This time it's even worse. I used full disc encryption. Luckily, I have about 80% of my data on backup. So it doesn't hurt that much. 

But I will try. I am cloning the hard disk into an image right now (DD), so I can test some things and become a bit smarter:
- testdisk to recover the partition table
- I will look into this: [http://serverfault.com/questions/318104/prevent-data-corruption-on-ext4-linux-drive-on-power-loss](http://serverfault.com/questions/318104/prevent-data-corruption-on-ext4-linux-drive-on-power-loss)
- And into repairing a broken super block: [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)


Any other ideas? Any ideas, what could be the reason for this? I'd understand why the ext4 partition would get corrupt, but why does the partition table get lost? Could it be faulty hardware? Perhaps the reason why my computer hang in the first place?

Thanks,

Matyy

---

### Post by oldfred on 2016-05-03
Partition table is just data on drive. And with power shutdown corruption occurs when data activity is not fully complete. I would not think you would lose partition table with forced power down.
But I suggest changing to gpt partitioning even if BIOS only system as one of its advantages is a backup partition table. If hardware is BIOS only and you dual boot with Windows on same drive you have to keep MBR(msdos) as Windows only boots from gpt with UEFI.

Also do not force shutdown. 
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/) 

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---


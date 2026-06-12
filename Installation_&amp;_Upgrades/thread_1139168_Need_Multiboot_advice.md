---
title: "Need Multiboot advice"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Canislupus on 2009-04-26
I know there are a lot of threads out there on multiboot, but I cannot seem to find one that covers my needs yet.

Here is my current setup:
```

Model: ATA ST31000340AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Size    Type      File system  Flags	Contents
 1      75.5GB  primary   ntfs              	WinXP
 2      210MB   primary   ntfs         boot 	win7 bootloader
 3      43.7GB  primary   ntfs              	Win 7 system
 4      881GB   extended               lba  	
 5      105GB   logical   ntfs              	empty
 6      315GB   logical   ntfs              	Data
 7      461GB   logical   ntfs              	Data

------------------------------------------------------------------------
Model: ATA ST3200822AS (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Size    Type      File system  Flags	Mount Point	Contents		
 1      403MB   primary   ext3         boot 	/boot		Linux/Ubuntu 		
 2      15.7GB  primary   ext3              	/		Ubuntu Jaunty (x86)
 4      32.6GB  primary   ext3              			{empty} (future 64bit Ubuntu OS)
 3      151GB   extended                    
 5      84.1GB  logical   ext3              	/home
 7      24.3GB  logical   ext3              	backups		{empty}
--	38.5GB		---- unallocated------
 6      1497MB  logical   linux-swap        	swapfile	Ubuntu swapfile

-------------------------------------------------------------------------
Model: ATA WDC WD800JB-00CR (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Size    Type     File system  Flags	Contents	
 1      41.9GB  primary  ntfs         boot 	WinXPold -- Old install (for disaster recovery and troubleshooting only)
---	38GB		---unallocated---

----------------------------------------------------------------------------

```


I am trying to meet as many of the following conditions as possible:

1)  	I prefer to use Ubuntu as my primary OS. Second place would be Win7, 
and Win XP is just there as a fall-back (or for when Win7 beta ends).

2)  	My boot partition is the second partition on the NTFS drive (sda2).  It doesn't have
to be, but I need to swap SATA1 and SATA2 if I am going to use linux grub to boot everything

3)	I don't like the windows vista/seven bootloader.  I like the troubleshooting options offered by grub, and it's a more attractive interface.

4)	I don't want to hide any partitions from any other installation (with the exception of the second XP install (WinXPold).  It is there only as a fail-safe, really.

5)	I have tried EasyBCD.  If Neogrub loaded --before-- Win7 bootloader, I wouldn't mind using it. As it is, if bootloader fails, the boot is dead in the water.

Any ideas?

---

### Post by pbpersson on 2009-04-26
I will reply to this one, however this is just my opinion.

One terabyte drives are $100 now.

Get a new one TB drive, drop it into the machine, move your data OFF sda and then unplug all the other drives and setup all your operating systems on sda using Grub.

I have a machine here running seven operating systems and it worked like a charm.  However, when I had three drives in there it was much too difficult to control what was happening and I did not know how to edit the Grub menu.

Then after you have all the Operating systems installed, plug in the data drives and link to them.

That is what I would do.  It makes it WAY easier, IMO

---

### Post by Canislupus on 2009-04-27
pbpersson:

Thanks for the input! That does sound like it would simplify things a lot.
I'm pretty convinced I want grub to be my primary boot manager. 

I may have enough storage to do that without spending the $100, even. It might take some shuffling and risk some data loss, but I'm ok with that.

A couple of follow-up questions:

Should that first partition be Win32, then?  Or Ext3?

Should the win7 bootloader reside on the same partition as grub? Or on the partition win7 is on?

Which way did you guys do it?

---

### Post by pbpersson on 2009-04-28
I'm sorry, but now you are departing from what I did and I don't want to steer you wrong.

Windows is very picky about how it loads, how its world must appear, and it does not recognize Linux or GRUB, it just lives in its Windows World.

In my case all my Linux distros are on one physical drive and Windows is on another drive which I have not yet plugged in because I have not needed it.

When I add Windows there is special code I need to add in the GRUB menu to fool Windows into thinking it is booting from the first drive and not the second drive, then I think I use a "chainloader" command to invoke the Windows NTLDR.

Sorry I cannot be of more help, but there are quite a few articles on here of how other people dealt with GRUB along with sample GRUB menus.

---


---
title: "WD Portable Hard Drive works on Laptop, but not on Desktop"
date: 2009-11-27
forum: Hardware
---

### Post by xtiano77 on 2009-11-27
I purchased a Western Digital 250Gb portable drive (MyPassport) a few months ago. At first everything was working fine, so I put it away until today. When I plugged it in to my Desktop this morning it mounted and the icon showed up. Then I clicked the icon and opened Nautilus and when I tried to open a folder where I have stored some documents, the HD unmounted and I wasn't able to get it back. I unplugged it and re-plugged it but it didn't mount and began making a clicking noise. I then plugged it in to my laptop and it worked just fine without the clicking noise. After a while it displays the following messages:

"Could not find "/media/MyPassport"
"Please check the spelling and try again."
"MyPassport" could be found. Perhaps it has recently been deleted."

I then plugged an older 80Gb portable hard drive to the desktop and it worked just fine. Is there anything I need to configure differently? Thanks in advance for your help.

Desktop specs:

Intel Dual Core Quad Processor
Ubuntu 9.10, 64bit
2Gb Memory
ATI Graphics card
500Gb Hard drive

Laptop specs:

HP
Intel Dual Core
Ubuntu 9.10, 32bit
1Gb Memory
Intel Graphics card
160 Gb Hard drive

---

### Post by efflandt on 2009-11-27
Nothing special should be needed for WD Passport.  See what **sudo fdisk -l** shows for it or the Partition Manager (or Gparted if you have that installed).  When you plug in a USB cable, you should do it decisively, not weasel it in.  I lost data on a CF card in Linux years ago (when usb mass storage was relatively new) when trying to plug it into a card reader and did not seat it quick enough.  Linux asked if I wanted to format it, apparently because it had already been corrupted.

Do you have the default (vfat) partition on the drive?  I even shrunk the vfat partition on a 160 GB Passport with gparted-live CD and installed a regular bootable Ubuntu 64-bit 9.10 system with grub in Passport mbr, and a swap partition.  When I connect it to either my desktop or laptop, either automounts both the WD Passport (vfat) and ext3 partitions.  And either computer boots 64-bit fine from the Passport (quieter than my desktop hard drive).  Never had any trouble with another 160 GB Passport either used for other Windows backup.

desktop: Athlon64 3200+ (earlier 2 GHz)
9.10 64-bit
2 GB RAM
ATI Radeon X1300 (default modules)
200 GB drive

laptop: Intel Dual Core 1.6 GHz
9.10 32-bit (capable of 64-bit)
1 GB RAM
Intel graphics
160 GB drive

I sometimes mess up a 4 GB USB stick by formatting the drive instead of partition while trying various live/install systems on bootable USB.  But I just recreate the partition (or partition table if necessary) with gparted.

Note that adding or removing partitions does not necessarily corrupt the data if you recreate partitions exactly as they were.  I had to recreate partitions on my current desktop with Linux fdisk when WinXP64 beta changed my cyls/heads years ago (could not even boot itself), and everything was fine once I got partitions corrected (no data loss).  Although, formatting can make it difficult to retrieve data.

---

### Post by xtiano77 on 2009-11-27
This is what "sudo fdisk -l" showed:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d5cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60052   482367658+  83  Linux
/dev/sda2           60053       60801     6016342+   5  Extended
/dev/sda5           60053       60801     6016311   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)



Maybe I posed the thread too soon. After I submitted the original post I tried an older USB cable that came with an older Segate 60Gb drive and the drive worked just fine. I copied files into it, unplugged and re-plugged various times and it hasn't given me any errors. I tried the original cable and the errors and clicking noise returned. Is there anything wrong with using an older cable? Also, would it hurt the drive if I format it with Linux? I mean, would I be able to use it on a Windows machine after being formatted with Linux?

---


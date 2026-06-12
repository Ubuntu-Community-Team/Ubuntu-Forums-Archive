---
title: "[SOLVED] Grub, RAID, and windows"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by sewerzuk on 2008-12-31
I'm a newb to Linux; have a little understanding of unix commands and am successfully running Intrepid on my Laptop, so I decided to install on my desktop.  I've run into a bit of a snag and after 2 days of searching for answers (found several similar posts but nothing I found seemed to work with my particular situation) and trying everything I can think of, I decided to ask for help. 

I am dual-booting into a system with 5 hard drives:
Windows XP is installed on /dev/sda and /dev/sdb in a SOFTraid controlled by my MB.
Ubuntu is installed on /dev/sdd.  I have installed GRUB on this device.
The other 2 drives are for storage/backups and are not bootable

I can choose in my BIOS whether to boot from the RAID array or /dev/sdd; as expected, booting from the raid loads XP fine, booting from sdd loads GRUB (and I can boot into Intrepid this way).  Because I didn't install DMRAID, Intrepid did not automatically detect my windows installation and did not make a menu.lst entry for booting into XP, so I made my own entry. Choosing which OS to boot with my bios settings is not very elegant and takes quite a bit of time.  I would like to be able to choose windows or Ubuntu with GRUB.  I can't figure out how to do this; seems like it should work fine but with my current setup when I try to boot into XP using GRUB I get the following error:
Error 13:  Invalid or unsupported executable format

Here is my fdisk -l output:

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0acd0acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24376   195800188+   7  HPFS/NTFS

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72488472

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+  42  SFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8ebf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30025   241175781   83  Linux
/dev/sdd2           30026       30401     3020220    5  Extended
/dev/sdd5           30026       30401     3020188+  82  Linux swap / Solaris

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a030a03

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19456   156280288+   7  HPFS/NTFS



And here is the important portion of my menu.lst:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d46f5c66-2f7c-4c4b-93d8-01520c0f489a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d46f5c66-2f7c-4c4b-93d8-01520c0f489a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d46f5c66-2f7c-4c4b-93d8-01520c0f489a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d46f5c66-2f7c-4c4b-93d8-01520c0f489a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d46f5c66-2f7c-4c4b-93d8-01520c0f489a
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I've tried all manner of different entries in my menu.lst; the one I have currently is the one that I think should work.  What am I missing?  Help!

---

### Post by caljohnsmith on 2008-12-31
How about trying all four of these entries in your menu.lst for Windows:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows XP (hd3)
rootnoverify     (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title       Windows XP (hd4)
rootnoverify     (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
Since you have five HDDs, Windows has to be on one of the other four drives different than Ubuntu, but since I don't know which drive Windows is in your BIOS boot order, you'll have to try all four possibilities. Or if you wanted to be more scientific about it, you could figure out which drive Windows is in the BIOS boot order, but I think it is probably easier just to give all the above entries a try. Let me know how it goes, and if none of the above entries work, please let me know exactly what happens when you try each one from the Grub menu. :)

---

### Post by sewerzuk on 2008-12-31
> **caljohnsmith said:**
> 
Since you have five HDDs, Windows has to be on one of the other four drives different than Ubuntu, but since I don't know which drive Windows is in your BIOS boot order, you'll have to try all four possibilities. 

Thanks for the reply!  I can tell you for sure that XP is on the raid array made up by these 2 drives:

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0acd0acc

Device Boot Start End Blocks Id System
/dev/sda1 * 1 24376 195800188+ 7 HPFS/NTFS

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


Is there a possibility that they may be in a different order when the BIOS lists them than my fdisk -l list?  
I'll try the 4 entries you gave me; I'm assuming that the map commands "fool" windows into thinking it is booting from the first drive in the device list?  Is this necessary for windows to boot?

edit:
I've tried booting from hd0,0 hd1,0 hd2,0 hd3,0 and hd4,0 before without using the map commands

---

### Post by caljohnsmith on 2008-12-31
> **sewerzuk said:**
> 
Is there a possibility that they may be in a different order when the BIOS lists them than my fdisk -l list?  
Yes, exactly; Grub on start up sees the order of drives as the BIOS boot order, not as how Linux orders the drives in /dev. So (hd0) is the drive you boot off of, and (hd1) is the 2nd boot drive, (hd2) is the 3rd boot drive, etc. So if you boot the Ubuntu sdd drive on start up, it would be (hd0), and all the other drives will be (hd1), (hd2), etc. 
> **sewerzuk said:**
> 
I'll try the 4 entries you gave me; I'm assuming that the map commands "fool" windows into thinking it is booting from the first drive in the device list?  Is this necessary for windows to boot?
Again, you're exactly right; unless you modify Windows XP's boot.ini file, then Windows normally needs to boot from the first boot drive or (hd0). Grub is sophisticated enough that it can fool Windows into thinking it is booting from the 1st boot drive by using Grub's "mapping" technique. :)

---

### Post by sewerzuk on 2008-12-31
Bingo!  The first entry worked.  And I learned something new.  It is a good day.  
Thanks!

---


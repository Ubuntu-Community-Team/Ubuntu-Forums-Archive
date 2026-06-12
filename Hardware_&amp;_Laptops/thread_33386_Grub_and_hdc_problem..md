---
title: "Grub and hdc problem."
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by The_Boy_Roger on 2005-05-10
Hi
I've been getting nowhere with this problem for days, I can't find anything
similar with google or other forums.

The problem is this; when I boot to ubuntu via grub, hdc, which is my cd/dvd
drive, isn't found.

If grub points to the wrong drive for root and stops with an error which
I then edit and correct, hdc is then found during the subsequent boot .

dmesg with correct grub menu:

# dmesg |grep hd
Kernel command line: root=/dev/hdd1 ro  splash
   ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
   ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
hda: Maxtor 6Y120L0, ATA DISK drive
hda: max request size: 128KiB
hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, 
UDMA(100)
hda: cache flushes supported
hdd: Maxtor 84320D4, ATA DISK drive
hdd: max request size: 128KiB
hdd: 8439184 sectors (4320 MB) w/256KiB Cache, CHS=8930/15/63, UDMA(33)
hdd: cache flushes not supported
Adding 208804k swap on /dev/hdd5.  Priority:-1 extents:1
EXT3 FS on hdd1, internal journal
SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)


dmesg with grub error which is corrected when it halts:

 # dmesg |grep hd
Kernel command line: root=/dev/hdd1 ro  splash
   ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
   ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
hda: Maxtor 6Y120L0, ATA DISK drive
hda: max request size: 128KiB
hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, 
UDMA(100)
hda: cache flushes supported
hdc: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive
hdd: Maxtor 84320D4, ATA DISK drive
hdd: max request size: 128KiB
hdd: 8439184 sectors (4320 MB) w/256KiB Cache, CHS=8930/15/63, UDMA(33)
hdd: cache flushes not supported
Adding 208804k swap on /dev/hdd5.  Priority:-1 extents:1
EXT3 FS on hdd1, internal journal
hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB


Active bits of grub menu.lst:

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdd1 ro  splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
map		(hd0) (hd2)
map		(hd2) (hd0)
root		(hd2,0)
savedefault
makeactive
chainloader	+1



Any help please, before I go insane!
Thanks
Roger

---

### Post by spd106 on 2005-05-11
Hi, could you post your /etc/fstab, this will show what should be mounted at boot time.

I take it you have no trouble with it in windows xp?

Could you also describe the error in grub, ie what stage and any messages.

---

### Post by The_Boy_Roger on 2005-05-11
Hi, thanks for replying.

Fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

The only way I can get hdc installed is as follows:

When the grub menu comes up on startup, with "Ubuntu, kernel 2.6.10-5-386" selected I hit edit.   I edit the line 'Root (hd1.0)' to read 'Root (hd0.0) and then hit boot.  This causes grub  to halt with the following screen:

Root (hd0.0)
    Filsystem type unknown, partition type 0xf
   Kernel  /boot/linuz-2.6.10-5-386  root=/dev/hdd1  ro splash

  Error 17:  Cannot mount selected partition

Press any key to continue

So I hit any key and again edit the root back to the correct location (hd1.0)

Now when I hit boot linux loads and finds my hdc.

Once ubuntu is loaded mounting is not a problem if hdc was found on boot, if it wasn't ofcourse it can't be mounted.

If I let grub run normally on startup linux loads without any error message but fails to find hdc.

What I was going to try next is installing ubuntu to  partitions on my first hd hda, my thinking being that ubuntu is confused by the fact that its installed on a drive after hdc ie hdd.

Here's my partition table for info:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/hda5               2       14946   120045681    7  HPFS/NTFS

Disk /dev/hdd: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         499     4008186   83  Linux
/dev/hdd2             500         525      208845    5  Extended
/dev/hdd5             500         525      208813+  82  Linux swap / Solaris

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9836    79007638+   7  HPFS/NTFS
/dev/sda2            9837        9964     1028160    f  W95 Ext'd (LBA)
/dev/sda5            9837        9964     1028128+   6  FAT16

---

### Post by spd106 on 2005-05-11
Hi, with my admittedly limited experience with grub and bootloaders in general, i can't see any problems with your setup. I don't know how you came up with the work around...? I suppose it could be bug (read feature).

Pehaps you are right in suspecting an issue with the naming. If i were you i'd reinstall on the primary disk, just as you suggested.

Sorry i wasn't any help.

 
ps just out of interest, what happend to hdb?

---

### Post by alastair on 2005-05-11
"ps just out of interest, what happend to hdb?"

hda == primary master (ide0)
hdb == primary slave (ide0)

If one is not connected, the device is not present.

As to the problem -  I can't see how this is an OS or GRUB issue. It seems to be living in BIOS-land. I would have a look through the BIOS and see if anything appears relevant. Perhaps something like "plug and play" .... who knows.

---

### Post by The_Boy_Roger on 2005-05-12
[QUOTE=alastair]"ps just out of interest, what happend to hdb?"

hda == primary master (ide0)
hdb == primary slave (ide0)

If one is not connected, the device is not present.

As to the problem -  I can't see how this is an OS or GRUB issue. It seems to be living in BIOS-land. I would have a look through the BIOS and see if anything appears relevant. Perhaps something like "plug and play" .... who knows.[/QUOTE]
 Thanks for your help guys

I moved my hdd ,which holds my ubuntu installation, from ide ch2 slave to id ch1 slave so its now hdb and its solved the problem.  Ubuntu boots ok and finds hdc (CD/DVDRAM) with no problem.

Thanks again
Roger.

---


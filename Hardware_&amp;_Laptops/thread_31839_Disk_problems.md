---
title: "Disk problems"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by zkissane on 2005-05-04
First, the hardware:
I have an Asus A7N8X Deluxe motherboard, with a Seagate 250GB SATA hard drive as my "main" drive (/dev/sda1-5).  It has both Ubuntu and Windows installed on it.  My other hard drive is a Maxtor 80GB (P)ATA133 drive, primary IDE chain, master drive (/dev/hda1 and 2), although it isn't being used for much at the moment (I migrated from the 80GB to the 250 last week and haven't bothered to reformat the 80GB yet).

I also have a MItsumi burner, secondary IDE chain, master, /dev/hdc; a no-name DVD-ROM, secondary IDE chain, slave, /dev/hdd; and a SCSI CD-ROM, although it's not the source of my troubles at this time, /dev/scd0.  

My first problem seems to be a typical one, judging by the search results, although I haven't been able to get any of the suggestions to work.  I can't enable  DMA for my DVD.  I've tried using hdparm:
```
zkissane@zkissane:~$ sudo hdparm -d1 /dev/hdd 
/dev/hdd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

zkissane@zkissane:/etc/rcS.d$ sudo hdparm /dev/hdd
/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```
I've tried editing hdparm.conf:
```
/dev/hdd {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

``` and that gets a similar "operation not permitted" on boot.

I've renamed /etc/rcS.d/S07hdparm to /etc/rcS.d/S99hdparm, no luck.

I've tried the "piix" trick in /etc/modules :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
mousedev
psmouse
sbp2
piix
ide-cd
ide-disk
ide-generic
lp

```

with no joy.  

Here's /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/c		ntfs	ro,auto,uid=1000,gid=1000 0 0
/dev/sda2	/d		ntfs	ro,auto,uid=1000,gid=1000 0 0
/dev/hda2	/maxtor		ntfs	ro,auto,uid=1000,gid=1000 0 0
```

I've seen some suggestions about chipset drivers being prerequisites for DMA, but I've not been able to locate any for my motherboard.  I'm running 2.6.10-5-k7 straight from apt-get.  

My second problem is more subjective.  My SATA drive seems sluggish.  I ran Debian back in 2001 off of an ATA33 drive and I remember it being snappier than what I have now.  For example, when I play mp3's, off of /dev/sda2 , my mouse skips across the screen at about 7 second intervals.  Here's hdparm on them...
```
zkissane@zkissane:/etc/rcS.d$ sudo hdparm /dev/sda3

/dev/sda3:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 13999426560, start = 324464805

zkissane@zkissane:/etc/rcS.d$ sudo hdparm /dev/sda2

/dev/sda2:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 150999690240, start = 29543535

```

I've read that hdparm isn't very good at tinkering with SATA drives, but it's better at doing PATA drives.  Are there better tools available for SATA, and/or are there tweaks that are safe with hdparm?

As always, help is appreciated.

---

### Post by Mr_Smiley on 2005-05-05
I'm having very similar problems aswell and so any help would be appreciated.

EDIT: Well I tried adding "piix" to the top of /etc/modules and that has fixed the problem for me. Sorry that I couldn't be of any help.

---


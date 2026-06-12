---
title: "dvdwriter now recognised as plain reader"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by MegaHz on 2007-04-06
Hello
suddenly after an apt-get dist-upgrade
I cannot use my dvdwriter as a dvdwriter, I can only use it as a reader.
Meaning that it can read all dvds and cds but when I run k3b or gnome
burner it does not recognize any writer. 
I don't know what went wrong,


this is my mount point entry:

megahz@megahz-desktop:/etc/init.d$ cat /etc/fstab | grep cd
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
megahz@megahz-desktop :/etc/init.d$

and this is my dmesg | grep hdd:

--------------------------------------------------
megahz@megahz-desktop:~$ dmesg | grep hdd 
[   25.162299]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings:
hdc:DMA, hdd:DMA
[    7.748000] hdd: _NEC DVD_RW ND-3520A, ATAPI CD/DVD-ROM drive
[    7.996000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache,
UDMA(33) 
[  119.616000] hdd: DMA interrupt recovery
[  119.616000] hdd: lost interrupt
[ 3347.800000] hdd: rw=0, want=68, limit=4
[ 3347.800000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16,
block=16
[ 3367.512000 ] hdd: rw=0, want=68, limit=4
[ 3367.512000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16,
block=16
[ 3375.236000] hdd: rw=0, want=68, limit=4
[ 3375.236000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16,
block=16 
[ 3410.932000] hdd: DMA timeout retry
[ 3410.932000] hdd: timeout waiting for DMA
[ 3410.932000] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest }
[ 3410.932000] hdd: drive not ready for command 
...
...
[ 3410.976000] hdd: drive not ready for command
[ 3427.356000] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest }
[ 3427.356000] hdd: drive not ready for command
[ 3427.356000 ] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest }
[ 3427.356000] hdd: drive not ready for command
[ 3427.356000] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest }
[ 3427.356000 ] hdd: drive not ready for command
[ 3427.360000] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest }
[ 3427.360000] hdd: drive not ready for command
[ 3427.360000] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest } 
[ 3427.360000] hdd: drive not ready for command
[ 3427.360000] hdd: status error: status=0x58 { DriveReady SeekComplete
DataRequest }
[ 3427.360000] hdd: drive not ready for command
[ 3559.256000] hdd: DMA interrupt recovery 
[ 3559.256000] hdd: lost interrupt
[ 3564.988000] hdd: DMA timeout retry
[ 3564.988000] hdd: timeout waiting for DMA
[ 3570.948000] hdd: DMA timeout retry
[ 3570.948000] hdd: timeout waiting for DMA
[ 3680.396000 ] hdd: DMA interrupt recovery
[ 3680.396000] hdd: lost interrupt
[ 3740.688000] hdd: DMA interrupt recovery
[ 3740.688000] hdd: lost interrupt
[ 3801.888000] hdd: DMA interrupt recovery
[ 3801.888000] hdd: lost interrupt 
[10423.216000] hdd: cdrom_decode_status: status=0x51 { DriveReady
SeekComplete Error }
[10423.216000] hdd: cdrom_decode_status: error=0x44 { AbortedCommand
LastFailedSense=0x04 }
[10429.228000] hdd: cdrom_decode_status: status=0x51 { DriveReady
SeekComplete Error } 
[10429.228000] hdd: cdrom_decode_status: error=0x44 { AbortedCommand
LastFailedSense=0x04 }
[10435.248000] hdd: cdrom_decode_status: status=0x51 { DriveReady
SeekComplete Error }
[10435.248000] hdd: cdrom_decode_status: error=0x44 { AbortedCommand
LastFailedSense=0x04 } 
[10441.284000] hdd: cdrom_decode_status: status=0x51 { DriveReady
SeekComplete Error }
[10441.284000] hdd: cdrom_decode_status: error=0x44 { AbortedCommand
LastFailedSense=0x04 }
[10441.284000] hdd: DMA disabled 
[10441.284000] hdd: ide_intr: huh? expected NULL handler on exit
[10441.332000] hdd: ATAPI reset complete
---------------------------------------------
--------------------------------------------------
my uname -a :
Linux megahz-desktop 2.6.20-14-generic #2 SMP Mon Apr 2 20:37:49 UTC 2007 i686 GNU/Linux


any ideas?

thanks

-- Andreas Constantinides

---

### Post by MegaHz on 2007-04-14
I'd like to tell you that this happens only when I enable DMA.
when I enable DMA then I cannot burn dvd.
when I disable DMA then is fine.

any solution?

---

### Post by MegaHz on 2007-04-14
well it semes tha thas nothign to do with DMA.

when I sudo k3b  (as root)
it burns OK.

can you tell me how to force default permissions to files (probably cdrecord) to have th ecorrect permissions?

---


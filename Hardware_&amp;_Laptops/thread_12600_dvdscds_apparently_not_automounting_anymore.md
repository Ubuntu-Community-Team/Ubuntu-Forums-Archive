---
title: "dvds/cds apparently not automounting anymore"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by hwu on 2005-01-25
hi there,

following prob: when i insert dvds/cds to my dvd/cdrom drive, it apparently 
isn't automounting anymore - it did work before, but recently somehow doesn't 
... 

i can mount /dev/cdrom (hdc) manually (except for audio cds - see further down 
below...) & apps work with that dvd-ro/cd-rw drive too (e.g. gnome-cd, ogle, k3b) 
... but the commands as defined & enabled in the respective gnome-control-center 
section don't ... as mentioned above, i also get an error msg, when trying to 
mount audio cds manually: 
```
 $ sudo mount -t iso9660 -o ro /dev/hdc /media/cdrom0
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       or too many mounted file systems
```
/media/cdrom0 dir & cdrom symlink are there...

/etc/fstab looks like the following:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /boot           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    umask=000       0       0
```
i checked dmesg & it gave me the following output (errors...):
```
 $ dmesg | grep hdc
    ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
hdc: UJDA740 DVD/CDRW, ATAPI CD/DVD-ROM drive
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 64
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1089072
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1088048
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1087824
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1089064
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1088040
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1087816
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1088472
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1087448
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1087224
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1088464
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1087440
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1087216
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 893604
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 892580
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 892356
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 893596
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 892572
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 892348
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 893004
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 891980
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 891756
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 892996
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 891972
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 891748
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1248
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 1024
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
```
please help...

---

### Post by mendicant on 2005-01-25
Looks like a hardware error to me.  Check the cable, perhaps?

---

### Post by grj on 2005-01-25
I cannot help with most of this, but you do not mount audio CDs. They do not have a file system. If I understand it correctly, audio apps use the device, not a mount point.

---

### Post by hwu on 2005-01-26
...ah ok, i didn't know that about audio cds (sorry, but i'm actually quite new to linux) 
... but apart from that it's imho really strange that i can mount the dvd/cdrw drive 
manually - but it doesn't work with automounting (anymore)..? ...

---

### Post by hashimoto on 2005-01-26
Updating kernel might solve this. I had similar problems with USB and CDROM with Warty. I'm now on Hoary and have no probs.

BR
Hashimoto

---

### Post by hwu on 2005-01-26
...thanks for the hints ... btw: i removed the drive from the laptop & built it in again 
meanwhile & desmg doesn't show errors with hdc anymore now:
```
 $ dmesg | grep hdc
    ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
hdc: UJDA740 DVD/CDRW, ATAPI CD/DVD-ROM drive
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
```
...but still automounting isn't working (only manually...) - so i'm considering updating 
the kernel to hoary ... could u give me advise how (& whether) to do that best, 
please..?

---

### Post by hwu on 2005-01-26
...hmm - i installed linux-image-2.6.10-2-386 from hoary repository by now & also 
re-installed gnome-volume-manager (warty version...) -> but still no go...  :-? ..?

---


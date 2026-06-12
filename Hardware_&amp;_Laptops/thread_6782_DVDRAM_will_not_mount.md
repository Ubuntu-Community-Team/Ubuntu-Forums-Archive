---
title: "DVDRAM will not mount"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by howiemoe on 2004-12-01
Hello,

Anybody's insight would be appreciated.  I'm having a problem getting my DVD writer working properly.  It is a USB iomega super DVD RW.  When I try and mount the disk CDROM2 from GNOME I get the error message:
[COLOR=DarkOliveGreen] mount: special device /dev/scd0 does not exist
[/COLOR]

Here is the partial output of dmesg

[COLOR=DarkOrange] usb 1-2: new full speed USB device using address 3
Initializing USB Mass Storage driver...

scsi0 : SCSI emulation for USB Mass Storage devices

  Vendor: HL-DT-ST  Model: DVDRAM GSA-4120B  Rev: A101

  Type:   CD-ROM                             ANSI SCSI revision: 02

sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray

Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0

USB Mass Storage device found at 2

usbcore: registered new driver usb-storage

USB Mass Storage support registered.[/COLOR]

contents of fstab
[COLOR=DarkSlateBlue]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/COLOR]

I'm new to linux, but I'd like to learn.  
thanks again,
jeff :-k

---

### Post by jdong on 2004-12-01
try **sr0** instead of scd0?

---

### Post by howiemoe on 2004-12-03
That worked perfectly thanks a bunch.  
It's nice when fixes are simple.
jeff

---


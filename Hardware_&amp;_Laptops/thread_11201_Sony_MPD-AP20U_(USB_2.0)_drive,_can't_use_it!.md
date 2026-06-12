---
title: "Sony MPD-AP20U (USB 2.0) drive, can't use it!"
date: 2005-01-14
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2005-01-14
Hi! 
I want to use my Sony MPD-AP20U external CDRW/DVD drive in ubuntu but I'm totally lost. When I plug in the drive to the usb 2.0 port, ubuntu recognize it (I can see it in device manager) but when I insert a CD in the drive, it doesn't get mounted like with my other drives, where an icon would appear in the desktop.

I never tried to use the drive under linux, but I remember reading it is supported under linux. Any suggestions??

Thanks again, great OS, great community.

[EDIT] this is my dmesg output after I plug it in:

> usb 6-5: new high speed USB device using address 3
scsi1 : SCSI emulation for USB Mass Storage devices
  Vendor: SONY      Model: CD-RW  MPD-AP20U  Rev: 1.0a
  Type:   CD-ROM                             ANSI SCSI revision: 02
sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
  Vendor: SONY      Model: MEMORYSTICK MPD   Rev: 1.0a
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 1
USB Mass Storage device found at 3
usb 6-5: reset high speed USB device using address 3
scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
scsi1 (0:0): rejecting I/O to offline device
scsi1 (0:0): rejecting I/O to offline device
scsi1 (0:0): rejecting I/O to offline device
SCSI error: host 1 id 0 lun 0 return code = 4000000
        Sense class 0, sense error 0, extended sense 0

---

### Post by KLineD on 2005-01-14
Turns out that when I restarted my computer, the output of dmesg says it recognized the drive and attached it to scsi0 but I can't find scsi0 anywhere, it's not in disks nor in /media/ where should I look up?

> SCSI subsystem initialized
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb 6-5: new high speed USB device using address 2
scsi0 : SCSI emulation for USB Mass Storage devices
  Vendor: SONY      Model: CD-RW  MPD-AP20U  Rev: 1.0a
  Type:   CD-ROM                             ANSI SCSI revision: 02
  Vendor: SONY      Model: MEMORYSTICK MPD   Rev: 1.0a
  Type:   Direct-Access                      ANSI SCSI revision: 02
USB Mass Storage device found at 2
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 1
sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0

Thanks!

---

### Post by KLineD on 2005-01-14
Well I got no answer, but I sorted it out.

For whatever reason, the drive doesn't get automounted, after reading trough the dmesg output, I did a:
```
mount /dev/sr0 -t iso9660 -r /media/cdrom2
```
and then I was able to read the content of the drive.

Still don't know why it doesn't get automounted...

---


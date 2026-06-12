---
title: "Asus T100ta weirdness"
date: 2015-05-17
forum: Hardware
---

### Post by J_Me on 2015-05-17
Kubutu 14.04 Asus T100ta
I have a usb extension cable(very basic male to female usb2) which I tried to use between a power brick and mini usb cable for charging a tablet, charging indicator light comes on but the thing will never charge. The cable works for anything else except for charging the tablet.
Also with the same tablet a external dvd drive keeps rebooting(the selection for 'available device' keeps on coming and going). The drive works with other computers, in fact the drive plugged into the extension cable will work on other computers. 

Is it the tablet that's messed up, What's going on.
```
After plugging in the dvd drive
dmesg | tail
[ 2892.205607] usb 1-1.2: Manufacturer: JMicron
[ 2892.205611] usb 1-1.2: SerialNumber: 28452D166322
[ 2892.206589] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[ 2892.207137] scsi1 : usb-storage 1-1.2:1.0
[ 2893.226012] scsi 1:0:0:0: CD-ROM            JLMS     XJ-HD166S        DS18 PQ: 0 ANSI: 0 CCS
[ 2893.230754] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 2893.230761] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 2893.231042] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2893.231198] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 2903.955857] [UFW BLOCK] IN=wlan1 OUT= MAC=macAddress SRC=192.000.0.254 DST=000.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=39193 DF PROTO=2

After loading a cd
dmesg | tail
[ 2967.320684] usb 1-1.2: SerialNumber: 28452D166322
[ 2967.322176] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[ 2967.323957] scsi6 : usb-storage 1-1.2:1.0
[ 2968.326201] scsi 6:0:0:0: CD-ROM            JLMS     XJ-HD166S        DS18 PQ: 0 ANSI: 0 CCS
[ 2968.328604] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 2968.328972] sr 6:0:0:0: Attached scsi CD-ROM sr0
[ 2968.329181] sr 6:0:0:0: Attached scsi generic sg1 type 5
[ 2968.370204] sr0: CDROM (ioctl) error, command: Xdread, Read track info 52 01 00 00 00 08 00 00 08 00
[ 2968.370224] sr: Sense Key : Medium Error [current] 
[ 2968.370229] sr: Add. Sense: Unable to recover table-of-contents
```

---

### Post by J_Me on 2015-05-26
bump

---


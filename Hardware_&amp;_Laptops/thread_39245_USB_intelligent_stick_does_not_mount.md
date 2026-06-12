---
title: "USB intelligent stick does not mount"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by dada on 2005-06-03
I am trying to access a 128MB USB stick. When I insert the stick it shows up on the desk top. But when I try to mount/acces it, it comes up with
"Error - Kio_mount helper"
"mount: can't find dev/sda in etc/fstab or etc/mtab" 
"Please check that the disk is entered correctly"

The dmesg result is below as is the mtab and fstab listing.

Can anyone help? Thanks heaps  

regards

Dada



dmesg result

usb 1-2: new full speed USB device using uhci_hcd and address 2
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: USB Card  Model: IntelligentStick  Rev: 2.23
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
SCSI device sda: 260032 512-byte hdwr sectors (133 MB)
sda: Write Protect is off
sda: Mode Sense: 0b 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 260032 512-byte hdwr sectors (133 MB)
sda: Write Protect is off
sda: Mode Sense: 0b 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: unknown partition table
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
---------------------------------------------------------
MTAB listing

/dev/hda7 / ext3 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda9 /home ext3 rw,commit=0 0 0
/dev/hda1 /media/win_C ntfs ro,uid=1000,gid=1000 0 0
/dev/hda5 /media/win_D vfat rw,umask=000 0 0
/dev/hda6 /media/win_E vfat rw,umask=000 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0

---------------------------------------

fstab listing

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,unhide,ro,noauto  0       0
/dev/hda1	/media/win_C	ntfs	ro,auto,uid=1000,gid=1000 0 0
/dev/hda5	/media/win_D	vfat    defaults,auto,umask=000, 0 0
/dev/hda6	/media/win_E	vfat    defaults,auto,umask=000, 0 0


------------------------------------------------------------------------

---


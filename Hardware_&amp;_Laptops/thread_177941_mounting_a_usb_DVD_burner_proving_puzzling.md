---
title: "mounting a usb DVD burner proving puzzling"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by russelld on 2006-05-17
Hi All

A usb DVD-RW is seen via lsusb, but not mounting and I can't find the /dev it sits on to get it to mount.

Wnen a differnet USB-harddisk mounts, it happens properly, so the USB system works.
When the USB-HD is plugged in, devs are created in /dev with consistent names like /dev/sda1, /dev/sda2 etc. However the dev names for the DVD-RW get a different dev name each time it is plugged, eg /dev/usb3.31 or /dev/usb3.33 or something else. So this makes it difficult to write a fstab entry to get it to mount. 

Finally, the USB-DVD burner does mount and reads/burns CD/DVD using the live CDs: Knoppix 3.6 , Ubuntu-Breezy, so it does work!

This is quite puzzling and I hope you can help in solving this.
TIA

this is what lsusb says:
```

 xxxx@xxx:~$ lsusb
Bus 003 Device 012: ID 067b:3507 Prolific Technology, Inc. <------ the housing for the DVD-RW
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0083 Microsoft Corp. <---------------MS Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

from /var/log/messages:
```

May 17 00:03:27 localhost kernel: [4316570.822000] usb 3-3: new high speed USB device using ehci_hcd and address 13
May 17 00:03:27 localhost kernel: [4316570.940000] scsi7 : SCSI emulation for USB Mass Storage devices
May 17 00:03:32 localhost kernel: [4316576.000000]   Vendor: LITE-ON   Model: DVDRW SHW-160P6S  Rev: PS08
May 17 00:03:32 localhost kernel: [4316576.000000]   Type:   CD-ROM                             ANSI SCSI revision: 00

```

/etc/fstab is:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>            <options>                 <dump>  <pass>
proc            /proc           proc              defaults                   0       0
/dev/hda2       /               ext3              defaults,errors=remount-ro 0       1
/dev/hda5       none            swap              sw                         0       0
/dev/hda6       /home           ext3              rw,users,exec,auto         0       1
/dev/hda7       /mnt/hda7       ext3              rw,users,exec,auto         0       0
/dev/hdc        /media/cdrom0   iso9660           ro,users,noauto,exec       0       0
/dev/sd0        /media/dvd      iso9660           ro,users,exec              0       0
/dev/sda1       /mnt/camera0    vfat              rw,user                    0       0
/dev/sda        /media/usb1     ext3              rw,user,exec,auto          0       0
/dev/sda1       /media/usb2     ext3              rw,user,exec,auto          0       0
/dev/sda2       /media/usb3     ext3              rw,user,exec,auto          0       0
/dev/sda3       /media/usb4     ext3              rw,user,exec,auto          0       0
/dev/sda4       /media/usb5     ext3              rw,user,exec,auto          0       0
/dev/sda5       /media/usb6     ext3              rw,user,exec,auto          0       0
/dev/sda6       /media/usb7     ext3              rw,user,exec,auto          0       0
/dev/sda7       /media/usb8     ext3              rw,user,exec,auto          0       0

```

---


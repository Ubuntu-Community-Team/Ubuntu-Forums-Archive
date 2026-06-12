---
title: "USB flash drive automatically mounts only for some media"
date: 2008-08-16
forum: Hardware
---

### Post by sayyeah on 2008-08-16
Hi all,
I'm using ubuntu 8.04.1 and when I insert my 8GB USB drive(EK memory) on my T61, I can see it in dmesg and gives a device ID(/dev/sdb1), but I have to mount manually as a root. (sudo mount -t vfat /dev/sdb1 ...) However, it perfectly works for other media(2GB, 1GB..).

I completely removed and reinstalled gnome-volume-manager but no luck.

Here's my dmesg.
```

$ dmesg|tail -n 20
[ 6837.563427] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.1/input/input26
[ 6837.629428] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-1
[ 6839.245899] usb 7-1: new high speed USB device using ehci_hcd and address 12
[ 6839.379069] usb 7-1: configuration #1 chosen from 1 choice
[ 6839.379346] scsi8 : SCSI emulation for USB Mass Storage devices
[ 6839.379634] usb-storage: device found at 12
[ 6839.379636] usb-storage: waiting for device to settle before scanning
[ 6840.039300] usb-storage: device scan complete
[ 6840.040476] scsi 8:0:0:0: Direct-Access     USB2.0   USB Flash Drive  0.00 PQ: 0 ANSI: 2
[ 6840.045156] sd 8:0:0:0: [sdb] 15794176 512-byte hardware sectors (8087 MB)
[ 6840.045784] sd 8:0:0:0: [sdb] Write Protect is off
[ 6840.045787] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6840.045789] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 6840.048402] sd 8:0:0:0: [sdb] 15794176 512-byte hardware sectors (8087 MB)
[ 6840.049032] sd 8:0:0:0: [sdb] Write Protect is off
[ 6840.049035] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6840.049037] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 6840.049042]  sdb: sdb1
[ 6840.112352] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 6840.112396] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

Here's by lsusb:
```

lsusb
Bus 007 Device 014: ID 1307:0165 Transcend Information, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 011: ID 413c:2105 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 016: ID 046d:c526 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

Another thing is, if I give usbfs instead of vfat for mount -t option, I only see directories of 001, 002, 003...until 007 with no files. I'm not sure this is normal.

I searched google for a while, but was not able to find any. Can somebody give me any hint on forcing ubuntu to mount automatically?

Thanks.

---

### Post by mpm on 2008-11-02
I had a similar problem in ubuntu 8.10, a Microcenter 8G USB wouldn't mount automatically and couldn't be mounted via nautilis.  I didn't try forcing the mount in the terminal.  What worked for me was mounting it on a Windows XP virtual machine first, and now it mounts automatically in ubuntu.

---

### Post by sayyeah on 2008-11-02
Thanks for the comment. I'll try later on my virtual machine. Unfortunately I lost my 8GB USB for now.. I'll post here when it works.

---


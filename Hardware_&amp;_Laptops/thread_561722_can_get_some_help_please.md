---
title: "can get some help please"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by rude_lee on 2007-09-27
i have an external drive that will not mount i keep getting a mount error
it used to mount fine then it mounted read only tried ntfs-config it did not give me write support at all so in the properties of the drive i put something in like read/write now it wont mount at all all i get is the mount error
how do i fix this

fdisk -l
gives me
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 11808 94847728+ 83 Linux
/dev/hda2 11809 12161 2835472+ 5 Extended
/dev/hda5 11809 12161 2835441 82 Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 60801 488384001 7 HPFS/NTFS

dmesg gives me
[ 580.716000] usb 3-4: new high speed USB device using ehci_hcd and address 3
[ 580.848000] usb 3-4: configuration #1 chosen from 1 choice
[ 581.068000] usbcore: registered new interface driver libusual
[ 581.092000] Initializing USB Mass Storage driver...
[ 581.092000] scsi0 : SCSI emulation for USB Mass Storage devices
[ 581.092000] usbcore: registered new interface driver usb-storage
[ 581.092000] USB Mass Storage support registered.
[ 581.092000] usb-storage: device found at 3
[ 581.092000] usb-storage: waiting for device to settle before scanning
[ 586.092000] usb-storage: device scan complete
[ 586.092000] scsi 0:0:0:0: Direct-Access ST350064 1AS E PQ: 0 ANSI: 2 CCS
[ 586.144000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[ 586.144000] sda: Write Protect is off
[ 586.144000] sda: Mode Sense: 00 38 00 00
[ 586.144000] sda: assuming drive cache: write through
[ 586.148000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[ 586.148000] sda: Write Protect is off
[ 586.148000] sda: Mode Sense: 00 38 00 00
[ 586.148000] sda: assuming drive cache: write through
[ 586.148000] sda: sda1
[ 586.164000] sd 0:0:0:0: Attached scsi disk sda
[ 586.188000] sd 0:0:0:0: Attached scsi generic sg0 type 0

need help bad really want this to work its pissing me off cuse i reformated and lost allmy stuff on there to see if it will work no dice

---

### Post by jppaynesr on 2007-09-27
You might consider changing the subject of your post from "can I get some help" to "external HD won't mount". I think you will get more hits.

---

### Post by eph1973 on 2007-09-27
What type of external HD is it (Manufacturer/Model)?  Is it brand new?  If it is, have you tried using GParted on it so set it up?  If you don't have GParted, you can get it by typing
```
sudo apt-get install gparted
```in the terminal.
If it has been existing, what type of file system is on it? (Looks like NTFS by your post, but a lot of the new external HD's come pre-formatted to NTFS).
If you have feisty, you might want to check out [this page]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") to ensure you have ntfs-3g installed and configured.
If you don't have feisty, which distro do you have?

---


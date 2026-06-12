---
title: "[SOLVED] External drive doesn't mount automatically"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by Tryfon on 2008-04-09
The problem is that my external hard drive doesn't **always** mount on startup and **almost** never when I plug it in with the computer on. But sometimes it does. How can this happen?
I checked out my fstab file and the hard drive (sdb1) is not mentioned there.
Of course I can mount it manually but I would prefer it to happen automatically **every** time. 
Any clue?

---

### Post by Rocket2DMn on 2008-04-09
If the drive is not unmounted properly, it won't automount when you plug it in.  That means if you just pull it out of a windows computer without safely removing it, it will not automount in linux, you have to force it to mount.  Also, if you don't "unmount" it from linux by either right clicking it on the desktop or using the "umount" command, it may not automount next time you plug it in.  This is all especially true with NTFS formatted drives.

---

### Post by Tryfon on 2008-04-10
That's something new! But unfortunately my external drive is ext3 formatted. Does the same apply here too?

---

### Post by Rocket2DMn on 2008-04-10
> **Tryfon said:**
> That's something new! But unfortunately my external drive is ext3 formatted. Does the same apply here too?

It may.  Next time you plug the drive in and it doesn't mount, post the output of 
```
dmesg | tail
```
That will show us the last few lines of some output that could be useful.
If you just do
```
dmesg
``` you will get a lot of more output, you might need to if using tail doesn't show us enough (you should see information related to detection of a new device, possible marked by sdb or whatever the device is detected as.
You can also try to run a filesystem check on the drive by plugging it in, making sure it's UNMOUNTED, and running
```
sudo fsck /dev/sdb1
```
where /dev/sdb1 is the device as shown in
```
sudo fdisk -l
```

---

### Post by Tryfon on 2008-04-11
Here is the dmesg output:

[18934.316000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[18934.464000] usb 5-6: configuration #1 chosen from 1 choice
[18934.764000] usbcore: registered new interface driver libusual
[18934.864000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[18934.864000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[18934.872000] Initializing USB Mass Storage driver...
[18934.872000] scsi2 : SCSI emulation for USB Mass Storage devices
[18934.872000] usb-storage: device found at 3
[18934.872000] usb-storage: waiting for device to settle before scanning
[18934.872000] usbcore: registered new interface driver usb-storage
[18934.872000] USB Mass Storage support registered.
[18939.872000] usb-storage: device scan complete
[18939.872000] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[18939.880000] sd 2:0:0:0: [sdb] Spinning up disk....ready
[18950.536000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[18950.540000] sd 2:0:0:0: [sdb] Write Protect is off
[18950.540000] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[18950.540000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[18950.540000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[18950.540000] sd 2:0:0:0: [sdb] Write Protect is off
[18950.540000] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[18950.540000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[18950.540000]  sdb: sdb1
[18950.572000] sd 2:0:0:0: [sdb] Attached SCSI disk
[18950.572000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[18951.152000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.21.1 DST=172.16.21.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[18951.152000] Unknown OutputIN= OUT=vmnet8 SRC=192.168.90.1 DST=192.168.90.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58


I also ran fsck for the drive and got this output:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Ext_500GB: recovering journal
Ext_500GB contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Ext_500GB: 25548/61063168 files (2.4% non-contiguous), 32944083/122096000 blocks

Still the drive won't mount automatically.

---

### Post by Rocket2DMn on 2008-04-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/126825](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/126825) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Tryfon said:**
> Here is the dmesg output:

[18934.316000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[18934.464000] usb 5-6: configuration #1 chosen from 1 choice
[18934.764000] usbcore: registered new interface driver libusual
[18934.864000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[18934.864000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[18934.872000] Initializing USB Mass Storage driver...
[18934.872000] scsi2 : SCSI emulation for USB Mass Storage devices
[18934.872000] usb-storage: device found at 3
[18934.872000] usb-storage: waiting for device to settle before scanning
[18934.872000] usbcore: registered new interface driver usb-storage
[18934.872000] USB Mass Storage support registered.
[18939.872000] usb-storage: device scan complete
[18939.872000] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[18939.880000] sd 2:0:0:0: [sdb] Spinning up disk....ready
[18950.536000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[18950.540000] sd 2:0:0:0: [sdb] Write Protect is off
[18950.540000] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[18950.540000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[18950.540000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[18950.540000] sd 2:0:0:0: [sdb] Write Protect is off
[18950.540000] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[18950.540000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[18950.540000]  sdb: sdb1
[18950.572000] sd 2:0:0:0: [sdb] Attached SCSI disk
[18950.572000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[18951.152000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.21.1 DST=172.16.21.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[18951.152000] Unknown OutputIN= OUT=vmnet8 SRC=192.168.90.1 DST=192.168.90.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58


I also ran fsck for the drive and got this output:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Ext_500GB: recovering journal
Ext_500GB contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Ext_500GB: 25548/61063168 files (2.4% non-contiguous), 32944083/122096000 blocks

Still the drive won't mount automatically.

Have a look at that bug report on launchpad, it seems to be the same problem you're having.  If you register on LP, you can make a post there and set the bug status to Confirmed.  Hopefully somebody will get to fixing that soon.  I know that FreeAgent drives can be a pain in linux, I have one myself that I use occassionally, though it is still formatted with ntfs. 
Since it has some power saving features, it tends to enter a low power state and unmounts itself from the system.  Then it fails to automount again unless the power on the drive is reset.  Seagate has been getting heat from linux users over the incompatibility of their drives with linux, so hopefully they will avoid the problem in the future, or newer version of linux (and Ubuntu in particular) will have built-in workarounds.

---

### Post by Tryfon on 2008-04-15
I installed Ubuntu 8.04 Hardy Heron and the problem is finally solved, once and for all! Drive mounts automatically every time I hot-plug it and every time I turn on my computer with the cable attached. Thank you all!

---


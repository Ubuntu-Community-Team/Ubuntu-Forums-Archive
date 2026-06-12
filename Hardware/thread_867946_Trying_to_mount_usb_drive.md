---
title: "Trying to mount usb drive"
date: 2008-07-23
forum: Hardware
---

### Post by lsutiger on 2008-07-23
I am trying to mount a usb drive,but do not know which /dev to match it to.
Here is what I get in dmesg:```
[166731.688323] usb 1-9: new high speed USB device using ehci_hcd and address 4
[166731.821595] usb 1-9: configuration #1 chosen from 1 choice
[166731.824845] scsi7 : SCSI emulation for USB Mass Storage devices
[166731.741300] usb-storage: device found at 4
[166731.741306] usb-storage: waiting for device to settle before scanning
[166736.731167] usb-storage: device scan complete
[166736.732276] scsi 7:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[166736.741941] sd 7:0:0:0: [sdd] Attached SCSI disk
[166736.741986] sd 7:0:0:0: Attached scsi generic sg4 type 0

```

It is not seen in Nautilus and fdisk -l:
```
Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0fac0fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1219     9791586   83  Linux
/dev/sdb2            1220        9606    67368577+  83  Linux
/dev/sdb3            9607        9730      996030   82  Linux swap / Solaris

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5cbc5cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdc2            2551        9038    52114860    f  W95 Ext'd (LBA)
/dev/sdc5            2551        9038    52114828+   7  HPFS/NTFS

```

/dev/sdb is my ubuntu disk, /dev/sdc is my old windows disk.

How can I list what disks are attached to the system?

---

### Post by wizardfait on 2008-07-23
> **lsutiger said:**
> 
[166736.741941] sd 7:0:0:0: [sdd] Attached SCSI disk


It appears to me it's mounted as /dev/sdd... however, why it doesn't show up in fdisk -l I don't know. Are you sure the USB drive is still connected? I've had a few drives that once they connect to a PC, they're active long enough to get the OS to load the driver, in time for it to die, so that the driver didn't start the device correctly, making it unusable.

I'd suggest, use another flash drive, see if it works in this computer (One you know works) and try this flash drive in another computer, and see if it works. Preferably another Ubuntu computer to see if it's possibly an Ubuntu bug, such as identifying it as the wrong drive, and loading the wrong driver?

---

### Post by lsutiger on 2008-07-23
It auto mounts my flash drive (just tested). The one I am having a problem with is a usb to ide/sata adapter.

It mounts fine in MS-WXP, so it is not the hardware.
I've had it work before, just not on this machine (work desktop). Don't have another ubuntu computer here.```
brian@brian-linux:~$ dmesg | tail
[172399.696317] usb 1-9: USB disconnect, address 6
[172427.657101] usb 1-9: new high speed USB device using ehci_hcd and address 7
[172427.791146] usb 1-9: configuration #1 chosen from 1 choice
[172427.795658] scsi10 : SCSI emulation for USB Mass Storage devices
[172427.796677] usb-storage: device found at 7
[172427.796681] usb-storage: waiting for device to settle before scanning
[172432.788861] usb-storage: device scan complete
[172432.790342] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[172432.714309] sd 10:0:0:0: [sdd] Attached SCSI disk
[172432.714348] sd 10:0:0:0: Attached scsi generic sg4 type 0

```

Also, for trying to mount:
```
brian@brian-linux:~$ sudo mount /dev/sdd /media/disk -t ntfs-3g
sudo: unable to resolve host brian-linux
Failed to read bootsector (size=0)
Failed to mount '/dev/sdd': Invalid argument
The device '/dev/sdd' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
brian@brian-linux:~$ sudo mount /dev/sdd /media/disk -t vfat
sudo: unable to resolve host brian-linux
mount: /dev/sdd: can't read superblock

```

I am 99% positive that it is an NTFS partition.

---

### Post by wizardfait on 2008-07-23
Ah, my apologies. I have no idea of Ubuntu's support for one of those... However, I've been wanting to get one, and I'd love to know the solution of your problem, if I do choose to get one. :D

---

### Post by lsutiger on 2008-07-23
Ok! I had this particular unit work on my 7.10 Laptop earlier this year. The disk attached showed up with fdisk -l

I'll keep on looking.

---


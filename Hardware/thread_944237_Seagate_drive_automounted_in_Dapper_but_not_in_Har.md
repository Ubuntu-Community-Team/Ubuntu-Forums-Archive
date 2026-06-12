---
title: "Seagate drive automounted in Dapper but not in Hardy or a fresh Intrepid Beta install"
date: 2008-10-11
forum: Hardware
---

### Post by gingermark on 2008-10-11
My Seagate portable USB harddrive will not automount when plugged in, and I don't know how to mount it.

It used to automount in Dapper no problem - one would just plug it in and it would work. My computer can detect it, output of lsusb is:

Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bc2:0502 Seagate RSS LLC
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have read about the *freeagent* problem - I don't believe my harddrive is one of these - the model number is ST30000U2 - and as I say, it worked in Dapper.

Curretly running Kubuntu Intrepid Beta (which is lovely), but this thing didn't work in Hardy either. It's very frustrating that things that used to work (in Dapper) stop working...

Thank you for any help.

---

### Post by gingermark on 2008-11-01
Please please can someone help.

sudo fdisk -l gives:
```
Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39c791b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       48641   390708801    c  W95 FAT32 (LBA)
```
This is crazy. The system can obviously see the drvie, knows it's fat32, knows where it is, why won't it automount??

How do I manually mount a USB harddrive?

---

### Post by gingermark on 2008-11-01
Ok, following on from the output in the last post have done the following manually, which seems to work:

```
sudo mkdir /media/seagate
``` (creating the mountpoint)

```
sudo chown -R gingermark:gingermark /media/seagate
``` (changing ownership of the mount point)

```
sudo mount -t vfat -o umask=000 /dev/sdd1 /media/seagate
``` (mounting the FAT32 drive to be able to be modified by all users...)


Now I just have to figure out how to safely unmount the thing, and maybe how to add this to the fstab permanently...

---


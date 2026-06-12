---
title: "Lacie USB HDD not able to mount"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by Mindspin85 on 2007-03-16
Got a problem here, i have a 40GB Lacie External Harddisk which is not recognized anymore.

When i just installed Ubuntu 6.10 i connected the hdd to my usb port and nothing happened, then when i restarted the system while keeping the disk connected it appeared on my desktop. Not a real pain to do cause most of the time i keep the disk connected.

Recently i booted my pc with the disk plugged into the usb and it didn't appear on my desktop, i tried manualy mounting it through the terminal and this is what i did:

```
matthijs@everest:~$ fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2            2230        9729    60243750    f  W95 Ext'd (LBA)
/dev/hdb5            2230        9729    60243718+   7  HPFS/NTFS

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    c  W95 FAT32 (LBA)
matthijs@everest:~$ sudo mount -t vfat /dev/sda1 /media/usb
mount: special device /dev/sda1 does not exist

```

So yeah that basically is what my problem is right now :P
Any thoughts?

---

### Post by Mindspin85 on 2007-03-16
I have nothing changed in my configs and all the sudden my disk is being recognized :)

---

### Post by etlpkby on 2008-04-03
Just want to mention this regarding LACIE USB disks - of which I have 500Mb USB2.0 version.

If you (for some reason) disconnect the power or usb cable when it is mounted - it will not remount - the little blue light will flash continuously - but it will not mount. This is what I have to do to fix it.

1. Switch off the Lacie disk.
2. Disconnect Power
3. Remove USB cable from system.
4. Reboot
5. Reconnect power cable
6. Attach USB cable.

Item (4) is recommended, but you can try and skip - your mileage will vary

I am running Ubuntu 8.04 (Heron Alpha6 on AMD64 - but this problem happened on Gusty 7.10 and FC4 before that.

Patrick/

---


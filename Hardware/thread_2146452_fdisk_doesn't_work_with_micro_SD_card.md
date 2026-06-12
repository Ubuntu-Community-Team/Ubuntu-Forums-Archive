---
title: "fdisk doesn't work with micro SD card"
date: 2013-05-18
forum: Hardware
---

### Post by LiSrt on 2013-05-18
I bought a micro SD card to replace a smaller capacity one in my phone,  but every time I tried to insert it, it automatically unmounted.

I figured it needed formatted, so I plugged it into a USB adapter on my computer.

However, when I try to run anything to do with partitions (partprobe, fdisk, gparted), it doesn't work when this particular card is connected.

fdisk hangs, gparted doesn't get past "scanning", and partprobe -s gives this:
```
udevadm settle - timeout of 120 seconds reached, the event queue contains:
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc (2622)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc/sdc1 (2623)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc (2626)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc/sdc1 (2627)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc (2628)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc/sdc1 (2629)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc (2631)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc/sdc1 (2632)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc (2633)
  /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.0/host12/target12:0:0/12:0:0:0/block/sdc/sdc1 (2634)

```


I'm pretty sure the card is /dev/sdc, what I'm suspecting is that it's a bad card - is there any way to actually tell?



EDIT:
Another command gets (sort of) useful information:

```

sudo fdisk -l | grep '^Disk'
Disk /dev/sda: 20.0 GB, 20014718976 bytes
Disk identifier: 0x0006fdcd
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
Disk identifier: 0x00050b8a
Disk /dev/sdc: 2196.1 GB, 2196102971392 bytes
Disk identifier: 0x00000000
```

sda and sdb are correct, but sdc should just be 32GB... :confused:

---

### Post by LiSrt on 2013-05-18
OK, either I've got a 2TB micro SD card, or something is seriously wrong - this is the output from fdisk, it didn't actually hang, just took a long time:
```
sudo fdisk /dev/sdc

Command (m for help): d
Selected partition 1

Command (m for help): d
No partition is defined yet!

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-4289263615, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-4289263615, default 4289263615): 
Using default value 4289263615

Command (m for help): p

Disk /dev/sdc: 2196.1 GB, 2196102971392 bytes
256 heads, 63 sectors/track, 265951 cylinders, total 4289263616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  4289263615  2144630784   83  Linux

Command (m for help): 

```

---

### Post by Mark Phelps on 2013-05-18
On all the phones I've used, the best approach is to format the SD card in the phone.  It can't mount it until it is formatted, so you have to format it first.

Usually, there's an option to do that.  Is that option greyed out on your phone?

---

### Post by LiSrt on 2013-05-19
> **Mark Phelps said:**
> On all the phones I've used, the best approach is to format the SD card in the phone.  It can't mount it until it is formatted, so you have to format it first.

Usually, there's an option to do that.  Is that option greyed out on your phone?

Yes, that was the first thing I tried - it's not even greyed out though, it just isn't there.  As soon as I insert the card, I get the message "SD card safe to remove", and the only option shown is to mount it (which doesn't work).

---

### Post by sudodus on 2013-05-19
Something is wrong when the phone does not accept the card.

- Is the hardware bad, or only the partition system?
- Or is the card too new (and/or too fast) to work with your phone and card adapter?

If you have a ***backup*** of your personal files (documents, photos ...) you can relax. Because the following command is risky.

You can try to overwrite everything that you can overwrite with zeros using ***dd***. But double check that you write to the correct drive, otherwise you might destroy your operating system.

```
 sudo dd if=/dev/zero of=dev/sdx
```

So replace x with the drive letter of the flash card. Check if it is still /dev/sdc

If it was possible to write those zeros, there is hope, and after that you can try ***gparted*** again.

If still no success, the hardware of the card is probably bad, or maybe of a kind, not compatible with your phone and card adapter.

---

### Post by LiSrt on 2013-05-20
I didn't get a chance to try dd as I was using a Windows machine today, so I tried formatting it on that - it seems to have worked, so if anyone else is in the same situation trying operations on multiple OSs might work.

---


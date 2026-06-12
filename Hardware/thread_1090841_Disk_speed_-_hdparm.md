---
title: "Disk speed - hdparm"
date: 2009-03-08
forum: Hardware
---

### Post by worjak on 2009-03-08
Hi,

I feel a bit dissatisfied with the disk speed of my IDE-disks: 

```
sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   266 MB in  2.01 seconds = 132.13 MB/sec
 Timing buffered disk reads:   84 MB in  3.02 seconds =  27.80 MB/sec

```

Then playing a round with hdparm would be the next step after getting the current state:

```
sudo hdparm /dev/sdb

/dev/sdb:
 IO_support    =  0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0

```

So what is this "HDIO_GET_DMA failed: Inappropriate ioctl for device" about? 

Is it a hw problem? lspci -v gives a lot of info but this is about the IDE stuff, which I don't understand:

```
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]

```

I found a bug in launchpad but I'm not sure that it affects me. It seems likely though: [https://bugs.launchpad.net/ubuntu/+bug/228302](https://bugs.launchpad.net/ubuntu/+bug/228302) which points to libata: [http://linux-ata.org/faq.html#combined](http://linux-ata.org/faq.html#combined)

The solutions seems quite cumbersome as it involves editing the ftab, UUIDs and perhaps more? Is it the only way to go? 

The hardware is a really old Dual PIII. The distro is Hardy Server.

Regards Jakob

---


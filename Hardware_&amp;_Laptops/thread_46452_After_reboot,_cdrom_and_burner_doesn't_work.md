---
title: "After reboot, cdrom and burner doesn't work"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by LokeDK on 2005-07-04
I had to reboot from the reboot button on my computer, after that my cdrom and burner doesn't work. When I put a disc into the cdrom drive it just says a quiet sound and do nothing. With my burner, it does run the cd but it detects ALL cd's as Empty CD-R discs. I've also noticed, under booting ubuntu that it says something with /dev/hdd no such file or directory (and /dev/hdd is/was my burner).
With mounting my cdrom drive manually, it says no medium found. And there is... I've tried with other cd's too.

Hmm some info:

```

[loke@wombat ~]$ dmesg | grep hdc
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
hdc: PLEXTOR CD-ROM PX-54TA, ATAPI CD/DVD-ROM drive
hdc: ATAPI 54X CD-ROM drive, 128kB Cache
[loke@wombat ~]$ dmesg | grep hdd
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
hdd: OPTORITECD-RW CW5205, ATAPI CD/DVD-ROM drive
hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache

```

Please help!

---

### Post by LokeDK on 2005-07-04
Hmm problem solved - I've tested with 3 cd's... and I guess I'm very unlucky that they're all broken? Tried with a Ubuntu cd.. works fine..

WEIRD

---


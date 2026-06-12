---
title: "Adeptec SCSI difficulties"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by dj_flx on 2005-08-22
I have a problem with the adeptec PCI SCSI card I've just installed in my machine; device manager recognizes it just fine, but can't see the drive (IBM 9GB).

lspci - 0000:00:03.0 SCSI storage controller: Adaptec AHA-2940U/UW/D / AIC-7881U

I tried installing the aic7xxx .rpm (converted to .deb) bat that didn't help.

I also can't seem to get to any configuration things for the card.

I am puzzled as to what to do next.

---

### Post by skoal on 2005-08-22
interesting...

I have:
> skoal@morpheus://~ $ lspci |grep -i scsi
0000:02:0b.0 SCSI storage controller: Adaptec AHA-2940U2/U2W

1. Is this a 2nd drive? What does cat /proc/partitions output?

2. Is the drive recognized at BOOT? Adaptec SCSI BIOS should report it found the drive and give stats when you hit <ctrl>-a.  (this is even before the grub screen and just after your IDE/memory is probed initially).

3. What kernel are you running? I'm on a custom 2.6.12 using the "aic7xxx" (new) driver.

\\//_

---


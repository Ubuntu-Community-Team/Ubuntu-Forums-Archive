---
title: "Plextor DVD burner"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by sjpritch25 on 2005-10-31
My drive was not detected when i installed Breezy badger.  here is the the version i have PX-712SA.  "SA" means SATA and i think that has a lot to do with the problem.  Luckly, i have an additional DVD drive.  Any thought on how to fix this would be great.  I have no idea ](*,)

---

### Post by jamieson on 2005-11-02
Same deal here.  BIOS sees the DVD drive just fine, but breezy does not detect it.  I can boot from the SATA DVD drive, which leads me to believe it's not a hardware problem... it's something in the kernel or libata module perhaps?

I've got a Soyo motherboard with VIA chipset.  There are no IDE devices.  Just one Seagate SATA drive (works fine) and the new Plextor SATA DVD drive.

---

### Post by sjpritch25 on 2005-11-02
[QUOTE=jamieson]Same deal here.  BIOS sees the DVD drive just fine, but breezy does not detect it.  I can boot from the SATA DVD drive, which leads me to believe it's not a hardware problem... it's something in the kernel or libata module perhaps?

I've got a Soyo motherboard with VIA chipset.  There are no IDE devices.  Just one Seagate SATA drive (works fine) and the new Plextor SATA DVD drive.[/QUOTE]


Samething i installed Ubuntu using my Plextor drive, however, its not detected.  I wonder how we can get this fixed??????????????

---

### Post by jamieson on 2005-11-05
Well, I finally just gave up on this problem and returned the DVD burner and got the PATA version.  Works fine now.  I think we'll just have to wait for libata support to improve and the SATA-PCI chipset manufacturers (VIA, Silcon Image, Intel, etc.) to get their stuff together.

I tried compiling various kernels (2.6.12, 2.6.14) and changing the libata.h file, enabling SCSI CDROM, etc.  Even tried other distros: Knoppix, Fedora core 4.  Nothing worked... except Windows XP... right out of the box with no patches.  Sadly Linux hardware support will always be lagging behind windows.  (Plextor probably ships the new drives with a hardware engineer to Redmond to get the drivers right.)

:???:

---


---
title: "SATA hard drive not found: sata_sis not working with ASUS T2 (SiS 760GX)"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by jcspray on 2005-10-16
Motherboard: ASUS T2
Chipset: SiS 760GX
One SATA hard drive.

lspci says:
0000:00:05.0 IDE interface: SiS: Unknown devices 0182 (rev 01)
0000:00:05.0 0101: 1039:0182 (rev 01)

With ubuntu breezy install disc, hardware detection picks up only /dev/hda (the cdrom device).  There are no other /dev/hd* or /dev/sd* drives.

When I switch to a terminal and do "modprobe sata_sis" (which should be the right driver for this motherboard), the line ```
libata version 1.11 loaded
``` appears in dmesg, but no new device nodes appear.

Any suggestions?

---

### Post by jcspray on 2005-10-16
It turns out that this device is not supported in linux 2.6.13.4, but there is a separate driver available from SiS which is meant to support it.

---


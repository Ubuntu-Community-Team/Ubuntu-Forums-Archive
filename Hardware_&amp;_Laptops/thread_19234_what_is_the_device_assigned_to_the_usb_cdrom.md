---
title: "what is the device assigned to the usb cdrom?"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by lorap on 2005-03-11
thanks
pavel

---

### Post by Thorongil on 2005-03-11
[QUOTE=lorap]thanks
pavel[/QUOTE]
 Normally, USB devices are hooked to the system as SCSI devices in the order of their connection.

/dev/sda to /dev/sdz

For a CDROM look directly for these device nodes, for hard drives you should  try the partition nodes sd[x][n]..

---


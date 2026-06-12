---
title: "Tape Drive not recognised as scsi"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by dmbeer on 2007-04-01
Hi All

I am trying to use my Tape Drive with Edgy, I can comunicate with the drive and read and write. The problem is that the status is not comming back sensibly because it is not setup to use ide-scsi. The drive should be using scsi emulation but when I added the following line to grub hdg=ide-scsi I get no device added.

How do add the tape ide scsi module in the kernel I have installed mt-st for communication with the device.

Thanks

David

---

### Post by dmbeer on 2007-04-03
OK This is not good news.

Any suggestions on getting proper ide-scsi support for my Tape Drive.

David

---


---
title: "SCSI problem"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by Tibor60 on 2006-01-28
My HP Scanjet 6300C scanner in not detected, but I think it is an SCSI detecting problem. The BIOS shows the Initio 9100UW scsi card, and the HP scsi device, but the ubuntu linux can not find the SCSI kontroller and any SCSI device.

(Tried to detect with the lsscsi and scsiadd -s commands, no success)

---

### Post by ChillyWilly on 2006-03-15
You could try this:

sudo modprobe initio

I have an initio 9400 and have to do this from a Terminal window
to have it recognize my SCSI HD's

---


---
title: "Can I use a DDS-5 tape drive with Ubuntu to do backups?"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by RoboJ1M on 2008-03-17
Hi,

Can I use a DDS-5 tape drive to do backups in Ubuntu?

Specifically an HP Model C1555-69202, there's a second hand one I can buy cheap. It's a 36/72 Gb model.

Anybody have any knowledge about using these under Linux/Ubuntu?

Thanks,

J1M.

---

### Post by RoboJ1M on 2008-03-17
I've been looking around, there are lots of these drives going cheap second hand.
They all appear to be SCSI and USB2 drives.

Is there anything special about these drives or will they just appear as /dev/sd<x>?

J1M.

---

### Post by dsotes on 2008-07-20
if you can see tape drive by executing

cat devices cat /proc/scsi/scsi

(something like this)

Attached devices:
Host: scsi0 Channel: 00 Id: 06 Lun: 00
  Vendor: ARCHIVE  Model: Python 06408-XXX Rev: 8071
  Type:   Sequential-Access                ANSI  SCSI revision: 03

you will probably habe this drive mapped to /dev/st0, so you can do

tar -zcf /dev/st0 /home/myuser

(or other tar options)

previously, mt command (man mt) allows you to rewwind, forward, eject, erase, etc...  tape mediums. For example

mt -f /dev/st0 erase



Good Luck

---

### Post by RoboJ1M on 2008-07-21
Is it like with other drives in Ubuntu? I plug them in and it all just works (SATA HDD, IDE DVD-RW, etc)?

How do I find out which ones "just work"?

Thanks!

J1M.

---

### Post by scorp123 on 2008-07-21
> **RoboJ1M said:**
> Can I use a DDS-5 tape drive to do backups in Ubuntu? Specifically an HP Model C1555-69202, there's a second hand one I can buy cheap. It's a 36/72 Gb model.

Anybody have any knowledge about using these under Linux/Ubuntu? We use tons of those in our server rooms. Work tip top.

SCSI tape drives show up as e.g. **/dev/st0** and **/dev/nst0**  (**_S_**CSI **_T_**ape = "st"). The "n" is for "non-rewinding", hence "nst0" (the other one might auto-rewind once a job is done ... you may or may not want this).

---

### Post by scorp123 on 2008-07-21
> **RoboJ1M said:**
> Is there anything special about these drives or will they just appear as /dev/sd<x>?  "sd" = **_S_**CSI **_D_**isk ... therefore: No. Tape drives will show as /dev/st0 and /dev/nst0 ...

---


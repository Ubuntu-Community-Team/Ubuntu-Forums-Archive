---
title: "Boot up problem with FreeAgent Go 500GB USB"
date: 2010-10-30
forum: Hardware
---

### Post by Dr.Fuzzy on 2010-10-30
My Ubuntu 10.10 refuses to complete the boot process and remains forever on the loading splash screen when my FreeAgent Go USB drive is attached. Only option is to hard reset my box. If the drive is not attached to the usb, it boots up normally and I can mount the disk as soon as I'm in the desktop environment. I've already set (through the seagate's tools in a winxp machine) the standby time to never.  

and this is what I get from sdparm:

sudo sdparm -a /dev/sdc

    /dev/sdc: Seagate   FreeAgent Go     102D
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     0  [cha: n, def:  1, sav:  0]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT         0  [cha: n, def:3000, sav:  0]

I've also attempted with no success to disable the USB legacy support BIOS option.

Some other USB hard disks and flash disks I tried cause no boot problem.

Really drives me crazy! Any ideas?

---

### Post by Dr.Fuzzy on 2010-10-30
No one? :(

---

### Post by IcarusR on 2010-10-30
Be patient, it's only 3 hours since you originally posted your situation !!

---

### Post by Dr.Fuzzy on 2010-11-01
null?

---


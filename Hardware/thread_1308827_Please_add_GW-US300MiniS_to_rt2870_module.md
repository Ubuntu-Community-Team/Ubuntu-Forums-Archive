---
title: "Please add GW-US300MiniS to rt2870 module"
date: 2009-10-31
forum: Hardware
---

### Post by skyborg007 on 2009-10-31
Hello everyone,

  I have recently bought a GW-US300MiniS by PLANEX in Japan.  After some googling I found that it requires the rt2870sta driver.  However the USB ID for this device is not yet present in the source file.

uname -a
Linux ubuntu-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

lsusb
Bus 002 Device 004: ID 2019:ab24 PLANEX 

{USB_DEVICE(0x2019,0xab24)}, /* Planex Communications, Inc. */
needs to be added to /usr/src/linux/drivers/staging/rt2870/rt2870.h at line 96

---


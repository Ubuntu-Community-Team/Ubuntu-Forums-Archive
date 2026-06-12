---
title: "iPhone 3GS with iOS4 does not show up in Ubuntu 10.04"
date: 2010-07-03
forum: Hardware
---

### Post by irrbloss on 2010-07-03
I did some googling on the topic and I have tried everything, still no luck getting the iPhone to work with Ubuntu. I've tried plugging in different types of usb-devices and check them with lsusb, all show up, but not the iPhone. I've tried different BIOS-settings and also tried ifuse, but still no luck. It works fine in Windows and OS X. Any ideas what to try next?

Hardware:
ZOTAC ION ITX F Series
iPhone 3GS with iOS4

Ubuntu Server x64 with following kernel:
Linux ---- 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux (also tried with 2.6.32-22).

---

### Post by mr_luksom on 2010-09-25
I realise it is a few months old, but nonetheless:

Not showing up at all in lsusb?

Is it possible to post dmesg tail after pluggin the iPhone in?

```
 dmesg | tail 
```

---


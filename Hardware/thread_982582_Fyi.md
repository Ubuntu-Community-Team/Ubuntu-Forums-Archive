---
title: "Fyi"
date: 2008-11-14
forum: Hardware
---

### Post by slikwill on 2008-11-14
I have a Toshiba Satellite A205-S5000 bought new in July 2008 and dual booting Ubuntu 8.04.1 and Windows Vista Home Premium(OEM).

This model has an SD reader slot in the front which works properly in Windows Vista but does not work in Ubuntu.  Inserting it while Ubuntu is running, the activity light associated with it lights for a second then goes out.  

SD cards are accessed by Ubuntu if used in a USB adapter.

---

### Post by cariboo on 2008-11-14
What is the output of dmesg when you plug an SD card into the card reader? So you don't get the whole output of dmesg in a terminal type:

```
tail -n 10 /var/log/dmesg
```

This will print out the last 10 lines of dmesg.

Jim

---

### Post by slikwill on 2008-11-14
[   41.165435] usbcore: registered new interface driver ndiswrapper
[   42.204647] cs: IO port probe 0x100-0x3af: clean.
[   42.206765] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   42.207653] cs: IO port probe 0x820-0x8ff: clean.
[   42.208404] cs: IO port probe 0xc00-0xcf7: clean.
[   42.209284] cs: IO port probe 0xa00-0xaff: clean.
[   42.383611] lp: driver loaded but no devices found
[   42.550752] Adding 787144k swap on /dev/sda6.  Priority:-1 extents:1 across:787144k
[   43.082873] EXT3 FS on sda5, internal journal
[   44.429906] ip_tables: (C) 2000-2006 Netfilter Core Team

I inserted a 1G SD card

---

### Post by slikwill on 2008-11-14
Additionally, 

I went to Places-> Computer and I see a "SD/MMC Drive" icon.

Double-clicking this gives "Unable to mount location" message

---


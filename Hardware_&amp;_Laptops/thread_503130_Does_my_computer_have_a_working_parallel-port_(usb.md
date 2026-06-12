---
title: "Does my computer have a working parallel-port (usb-parallel)"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by daller on 2007-07-17
Hi there,

I'm setting up a computer for my father-in-law, living over 100km away!

I have everything working (Kubuntu) - but I'm not sure if the usb-parallel cable I have bought, works with Linux...

How do I check?

This is lsusb:

```

christen@christen-desktop:~$ lsusb
Bus 002 Device 015: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 002 Device 004: ID 0461:4d15 Primax Electronics, Ltd
Bus 002 Device 003: ID 413c:2010 Dell Computer Corp.
Bus 002 Device 002: ID 413c:1003 Dell Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

And dmesg:

```

[ 1427.576000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 15 if 0 alt 1 proto 2 vid 0x067B pid 0x2305

```

Any ideas?

---


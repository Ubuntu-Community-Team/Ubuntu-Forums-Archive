---
title: "LaCie BigDisk 500 Firewire - not recognised"
date: 2006-05-03
forum: Hardware &amp; Laptops
---

### Post by marystern on 2006-05-03
Hello all,

I'm trying to use a LaCie BigDisk 500 with Ubuntu via a Firewire connection. It works fine on Windows (it's automatically recognised and usable when connected).

Under Breezy and Hoary, it doesn't appear at all automatically. 

What do I need to do to get the drive recognised and mount the drive?

(I'm an experienced Linux user, but haven't done anything else with Firewire),

Thanks,
Mary.

---

### Post by marystern on 2006-05-11
Hmm - and I thought Ubuntu was supposed to be a herlpful place?... :(

---

### Post by marystern on 2006-05-30
well, I can't get it working, and there's ZERO HELP, so I'm going back to Windows..which actually WORKS..another "great job" Linux community :((

---

### Post by wr0x2 on 2006-05-30
What does "dmesg | tail" output when you plug in the drive?

---

### Post by marystern on 2006-06-14
>> other firewire stuff from dmesg...

[4294704.052000] ieee1394: Initialized config rom entry `ip1394'
[4294717.052000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294717.113000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0002800-e0002fff]  Max Packet=[2048]
[4294718.380000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011060000000001]

>>> About to connect BigDisk...
[4295341.498000] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[00d04b4c1b057f16]
[4295341.498000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4295341.758000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4295341.758000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4295377.248000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023

>>> About to unplug  BigDisk...
[4295377.248000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00d04b4c1b057f16]

---


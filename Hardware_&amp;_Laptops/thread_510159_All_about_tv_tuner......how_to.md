---
title: "All about tv tuner......how to?"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by ajmal_82 on 2007-07-26
lspci -v output:
Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors Unknown device 0000
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at e8020000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1
Capabilities: <access denied>:confused:
**************
the system specs:feisty fawn,intel 845gvsr mobo,p4 2.8gig,80 gig seagate,lg monitor,realtek ethernet card not detected,Super tv card~philips chipset(under xp using christv detected as phtvtune)
saa7130 analogue card not dvb using cable in india/asia.
the dmesg first gave me output:unknown/generic card,then i ran command :"modprobe saa7134".then it gave above o/p.
now i want a solution to run atleast tvtime.:(

---


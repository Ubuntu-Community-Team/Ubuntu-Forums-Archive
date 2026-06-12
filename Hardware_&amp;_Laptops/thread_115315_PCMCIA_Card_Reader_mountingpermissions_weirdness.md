---
title: "PCMCIA Card Reader mounting/permissions weirdness"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by eosha on 2006-01-10
Hi there,

Brand new Sandisk PCMCIA 6-in-1 card reader. 512mb SD card. Sony Vaio FXA36 laptop.

dmesg says:

> 
[4346793.464000] Probing IDE interface ide2...
[4346793.728000] hde: Memory Card Adapter II, CFA DISK drive
[4346794.735000] ide2 at 0x100-0x107,0x10e on irq 3
[4346794.739000] hde: max request size: 128KiB
[4346794.739000] hde: 1000448 sectors (512 MB) w/1KiB Cache, CHS=1954/16/32
[4346794.739000] hde: cache flushes not supported
[4346794.744000]  /dev/ide/host2/bus0/target0/lun0: p1
[4346794.752000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0

which I'm interpreting to mean that it sees the card at hde. After creating /media/card, I added

> /dev/hde1       /media/card     auto    noauto,user,exec        0       0

to fstab (I also tried it with just /dev/hde).

When the card is inserted, it briefly mounts to the desktop, shows the correct name for the card, opens nautilus and shows the correct contents of the disk for a split second, then disappears and goes to my home directory. My instincts tell me that this is a permissions problem, but not one I'm smart enough to resolve. Help?

---


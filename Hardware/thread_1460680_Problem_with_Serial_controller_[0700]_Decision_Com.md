---
title: "Problem with Serial controller [0700]: Decision Computer International PCCOM8"
date: 2010-04-23
forum: Hardware
---

### Post by masjito on 2010-04-23
I put pccom8 multiport serial in ubuntu machine, but I only have 4 ttyS up in my system, here dmesg result for ttyS list on my pc (I have disabled onboard serials interface): 
> ~# dmesg |grep ttyS
[    1.689483] 0000:01:0a.0: ttyS0 at I/O 0xc400 (irq = 22) is a 16550A
[    1.689862] 0000:01:0a.0: ttyS1 at I/O 0xc408 (irq = 22) is a 16550A
[    1.690210] 0000:01:0a.0: ttyS2 at I/O 0xc410 (irq = 22) is a 16550A
[    1.690562] 0000:01:0a.0: ttyS3 at I/O 0xc418 (irq = 22) is a 16550A

and here lspci result for my pci device:
> ~# lspci -vnn
....
01:0a.0 Serial controller [0700]: Decision Computer 
International Co. PCCOM8 [6666:0002] (rev 01) (prog-if 02)
        Subsystem: Device [0008:0200]
        Flags: medium devsel, IRQ 22
        Memory at cdeffc00 (32-bit, non-prefetchable) [size=128]
        I/O ports at c800 [size=128]
        I/O ports at c400 [size=256]
        Kernel driver in use: serial
.....

anyone can give me a clue to make my pccom8 card can work with my ubuntu machine?

Thank you before :popcorn:

---

### Post by anglican on 2010-04-23
> **masjito said:**
> I put pccom8 multiport serial in ubuntu machine, but I only have 4 ttyS up in my system, anyone can give me a clue to make my pccom8 card can work with my ubuntu machine?

Thank you before :popcorn:

You will need the setserial package to configure multiple serial ports, by default Ubuntu only configures /dev/ttyS0-3.

H

---


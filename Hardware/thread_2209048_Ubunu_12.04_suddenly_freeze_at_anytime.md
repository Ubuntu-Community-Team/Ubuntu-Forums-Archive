---
title: "Ubunu 12.04 suddenly freeze at anytime"
date: 2014-03-03
forum: Hardware
---

### Post by nachollica on 2014-03-03
Hello!

I bought a new machine:
- Mother Gigabyte GA-H87M-D3H
- 8GB RAM Kingston HyperX red (DDR3, 1600 MHz)
-  Core i7 Haswell (4th generation)
- GeForce GTX 650 Ti
- Solid State Drive Kingston (60 GB)

I have installed Ubuntu 12.04 64bit and Windows 7 Home Premium SP1 64bit (both in the SSD). When I'm using Ubuntu, it suddenly hangs. The only thing I can do is to power off the PC. When using Windows, it happens but less frequently.
In Windows I have the last drivers for USB 3.0, chipset and AHCI. In Ubuntu, I can not get them. I hope the kernel supports it all.
When the computer freezes, dmesg shows something like "ata3.00: error". I am not sure what it said, and I can not read it again because after freezing, Ubuntu does not boot any more. So I think the problem comes from SSD.

I need help please. I have a new machine and can not use it :(

Thanks

---

### Post by phidia on 2014-03-03
Maybe reading through [this thread]("http://ubuntuforums.org/showthread.php?t=1034762") here at the forums can help you?

---

### Post by nachollica on 2014-03-06
I found that thread some days ago but it didn't help me. It isn't the same dmesg output than mine.

Here is my dmesg output:

ata6: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
ata6: irq_stat 0x00400040, connection status changed
ata6: SError: { HostInt PHYRdyChg 10B8B DevExch }

This page explains the libata errors:
[https://ata.wiki.kernel.org/index.php/Libata_error_messages](https://ata.wiki.kernel.org/index.php/Libata_error_messages)

I tried to understand my situation but I can't. Please help me, my new computer is completely unusable :(

---


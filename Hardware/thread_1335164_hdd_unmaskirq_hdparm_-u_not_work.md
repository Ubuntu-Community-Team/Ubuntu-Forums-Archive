---
title: "hdd unmaskirq: hdparm -u not work"
date: 2009-11-23
forum: Hardware
---

### Post by ambrosa on 2009-11-23
I'm using Ubuntu 8.04 LTS server 32 bit in a VIA EPIA mobo based on 1 Ghz C7 CPU
It runs fine but now I've a problem.
I've connected a serial device to /dev/ttyS0 and sometimes I've a "overrun" error.
After some tests and after reading many documents, the problem can be solved (perhaps) unmasking HDD irq

My system is equipped with a 2.5" 60GB HITACHI IDE HDD with standard PATA connector. Kernel recognize it as /sdev/sda

Unmasking is done with command:
*hdparm -u 1 /dev/sda*
but the response is:

[I]set unmaskirq to 1 (on)
HDIO_SET_UMASKINTR failed: inappropriate ioctl for device.
[/I]

Any solution ?

---

### Post by imrehg on 2009-12-11
I think the irq unmasking is only available with the IDE driver. But looking at your hard drive reference (/dev/sda) the kernel is automatically using the scsi driver (with IDE it would be /dev/hda), which does not have unmasking...

Probably there's a different solution for your original problem.

---


---
title: "Zoran chipset and Karmic"
date: 2009-11-07
forum: Hardware
---

### Post by alerinaldi on 2009-11-07
Hello,
I have this card:
```
vlad@vlad:~$ lspci | grep Zoran
04:05.0 Multimedia video controller: Zoran Corporation ZR36057PQC Video cutting chipset (rev 02)
```I read that this is supported by the zr36067 module, but this is what is said in dmesg about it:
```
[ 2500.139109] MJPEG[0]: Zoran ZR36067 (rev 2), irq: 20, memory: 0xfebff000
[ 2500.139115] MJPEG[0]: Subsystem vendor=0x1031 id=0x7efe
[ 2500.139164] IRQ 20/DC10plus[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 2500.149989] saa7110 1-004e: chip found @ 0x9c (DC10plus[0])
[ 2500.178656] adv7175 1-002b: chip found @ 0x56 (DC10plus[0])
[ 2500.191780] DC10plus[0]: zoran_probe - no codec found
```Someone can help me?
Thank you very much!

---


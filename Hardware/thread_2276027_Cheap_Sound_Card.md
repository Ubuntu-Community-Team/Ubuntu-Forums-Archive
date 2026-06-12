---
title: "Cheap Sound Card?"
date: 2015-04-29
forum: Hardware
---

### Post by mamamia88 on 2015-04-29
I have an old dell with a hissing built in sound card.  I have 2 pci slots and a mini pcie slot leftover.  Any recommendations for something cheap?   Don't really care about sound quality just want to get rid of the hiss

---

### Post by bcschmerker on 2015-04-30
ASUSTeK Computer, Inc., had produced some now-discontinued audio cards that are specifically built anti-hiss:  the XONAR® Essence™ ST™ (PCI 2.x), XONAR® Essence™ STX™ (PCIe 1.0 x1), and XONAR® Xense® (PCIe 1.0 x1).  All have integrated RFI shielding and are built around a modified C-Media® CMI-8788 DSP chip; and both the ST and STX have plug-in dual operational amplifiers for Left I-V, Right I-V, and Line-Output Buffer.  With ALSA 1.0.24 or later, use the Driver snd-virtuoso, which has specific tweaks to support the XONAR relay controls compared to snd-oxygen.

---


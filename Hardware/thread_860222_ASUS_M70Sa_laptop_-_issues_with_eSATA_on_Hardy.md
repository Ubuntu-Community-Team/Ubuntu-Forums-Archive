---
title: "ASUS M70Sa laptop - issues with eSATA on Hardy"
date: 2008-07-15
forum: Hardware
---

### Post by dehuszar on 2008-07-15
I just picked up a MONSTER laptop, the ASUS M70Sa, and I am super pleased with it.  Just about everything worked out of the box, or required minimal work to get going. 

The only thing not working right now is the eSATA controller.  Doing an lspci -l | grep ATA, I can see the following:

```
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
```

I am unable to see the drive doing lshw either.

I've read in other posts about people turning on AHCI in the BIOS, but sadly, the only BIOS entry regarding the SATA bridge is a selector between "Native" and "Compatible".  Switching to "Compatible" doesn't seem to have an effect.

Does anyone have any ideas?

---


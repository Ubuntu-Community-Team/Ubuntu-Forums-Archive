---
title: "Problems Installing Graphics Driver"
date: 2015-11-29
forum: Hardware
---

### Post by alan71 on 2015-11-29
So I'll keep this short, I have an R9 380 4GB AMD Graphics Card and after following this guide ([https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)) on how to install the driver, this is the output from 'fglrxinfo':

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: DID:6939 RID:F1
OpenGL version string: 4.4.13374 Compatibility Profile Context 15.20.1013

Why is it called: DID:6939 RID:F1 - Shouldn't it not say my GPU as I stated above? And as shown in the tutorial which I linked?

Thanks in advance for any answers! :)

---

### Post by QIII on 2015-11-29
Hello!

Which section of the instructions did you use?  What release of Ubuntu are you running?  Can you tell us more about your system hardware specs?

---

### Post by alan71 on 2015-11-30
I used part 3.1 and with the fglrx-updates version. The rest of my system is:

CPU: Intel Core i5-4460 3.4GHz Quad-Core Processor
Motherboard: MSI H81M-P33 Micro ATX LGA1150 Motherboard
Memory: Crucial Ballistix Sport 8GB (2 x 4GB) DDR3-1600 Memory 
Storage: Intel 535 Series 180GB 2.5" Solid State Drive
Storage: Seagate Barracuda 2TB 3.5" 7200RPM Internal Hard Drive
Video Card: MSI Radeon R9 380 4GB Video Card
Case: Cooler Master N200 MicroATX Mid Tower Case
Power Supply: XFX 550W 80+ Bronze Certified ATX Power Supply

---

### Post by Yellow Pasque on 2015-11-30
> Why is it called: DID:6939 RID:F1 - Shouldn't it not say my GPU as I stated above?
I doubt that affects the driver's function. Nevertheless, you can try this (needs internet connection):
```
sudo update-pciids
fglrxinfo
```

---


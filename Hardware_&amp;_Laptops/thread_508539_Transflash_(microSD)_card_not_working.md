---
title: "Transflash (microSD) card not working"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by flixer on 2007-07-24
My Transflash card is not working for Ubuntu. It's recognized by the kernel, but Hal doesn't do anything about it.
lspci:
```

06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:07.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

This is what happens in dmesg when insert the card and then take it out.
It only produces this, but it should produce more log than below.
```

[  364.432000] tifm_core: MMC/SD card detected in socket 0:3
[  548.900000] tifm0 : demand removing card from socket 0:3

```

---


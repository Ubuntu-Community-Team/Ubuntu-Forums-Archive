---
title: "NVidia card not AGP8X"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by fordfan753 on 2005-09-22
This is not a huge problem, but I'm just curious why my NVidia FX5500 card is only using 4X, when my motherboard and card can support 8X and I have the official nvidia drivers installed.  :???: 

```
darren@amdinside:/proc/driver/nvidia/agp$ cat card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000e1b:0x1f000301

darren@amdinside:/proc/driver/nvidia/agp$ cat host-bridge
Host Bridge:     VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000a0f:0x00000b01

darren@amdinside:/proc/driver/nvidia/agp$ cat status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Enabled
```

---

### Post by bob_c_b on 2005-09-22
A number of older VIA and SiS chipsets "cheated" with the AGP implementation so in the name of stability many times the nVidia driver reverts to 4x for stability purposes.

---

### Post by fordfan753 on 2005-09-23
[QUOTE=bob_c_b]A number of older VIA and SiS chipsets "cheated" with the AGP implementation so in the name of stability many times the nVidia driver reverts to 4x for stability purposes.[/QUOTE]

Thanks for the reply, but I'm not sure if my chipset would be classed as older. My specs are posted in my signature. I forget what exact chipset it is (I'm bad with remembering numbers) but I think it's a VIA KT600.

---

### Post by bob_c_b on 2005-09-23
[QUOTE=fordfan753]Thanks for the reply, but I'm not sure if my chipset would be classed as older. My specs are posted in my signature. I forget what exact chipset it is (I'm bad with remembering numbers) but I think it's a VIA KT600.[/QUOTE]

I ran into this on Mandrake 10.x, while not ancient by any means the KT600 is consiered legacy. It is typically supported at 4x in most distros and usually uses the same driver as the KT400 (but with a different PIC identifier). Both the KT600 and KT400 did some less than compliant things with AGP spec. I have run into similair issues with some of my older VIA boards. VIA has been much better behaved lately and their PCI-Express implementation is by the book, but I think you will find many of the older (lower than KT800 series) VIA chipsets default to AGP 4x under the vast majority of Linux installations. You might be able to force it, but definitely do some serious stability testing.

---


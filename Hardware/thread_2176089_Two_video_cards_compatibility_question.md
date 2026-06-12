---
title: "Two video cards compatibility question"
date: 2013-09-22
forum: Hardware
---

### Post by HardTrickySecurity on 2013-09-22
Hi

1) TV 2GB PCIEx16 ASUS HD6450 DDR3 VGA/DVI/HDMI/SILEN
[http://shop.amd.com/us/Manufacturer/Asus/Detail/GraphicCard/HD6450-SL-2GD3-L](http://shop.amd.com/us/Manufacturer/Asus/Detail/GraphicCard/HD6450-SL-2GD3-L)

2) T.VIDEO EVGA NVIDIA GEFORCE GT620 1GB 700MHZ DDR3 DVI HDMI 02G-P3-2625-KR
[http://www.evga.com/Products/Product.aspx?pn=01G-P3-2621-KR](http://www.evga.com/Products/Product.aspx?pn=01G-P3-2621-KR)


I dont know if this is the right place to ask this question. Feel free to move it.

I am about to buy a video card for my pc. Wich one of this two models you guys think will be more compatible and run smooth and without problems on Lubuntu 13.04.
I just dont want to have compatibility drivers problems.

Thanks

---

### Post by bcschmerker on 2013-09-23
Advanced Micro Devices® and nVIDIA® have a long history of driver conflicts even in Microsoft® Windows® 2000, XP, and 6-up, so it's a case of one or the other and not both in Ubuntu®.  My own experience is with ATi®/AMD® hardware; my "Hot Rod gPC®" currently packs an ATi® Radeon® HD 3200 in its AMD® 780G/SB710 chipset, and I've had no problems with xserver-xorg-video-radeon.  OtOH, I've had nothing but headaches with xserver-xorg-video-nouveau on a rebuilt eMachines®/Acer® EL1210-09 (nVIDIA® MCP78S chipset, includes GeForce® 8200 GPU).

The Asus® EAH6450SL/DI/2GD3(LP) is new enough to force the AMD® proprietary driver and settings application (packages: fglrx, fglrx-amdcccle) for now; X.org may have a new xserver-xorg-video-radeon that can drive it by the Release to Manufacture of 13.11a1 Trusty Tahr&#8482; (as 14.04.1-LTS) next year.

---


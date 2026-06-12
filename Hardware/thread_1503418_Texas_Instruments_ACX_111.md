---
title: "Texas Instruments ACX 111"
date: 2010-06-06
forum: Hardware
---

### Post by qrrbrrbbl on 2010-06-06
I had asked here for some wireless help a couple of weeks ago, and I've since moved closer to solving my problem. I learned that I had a Texas Instruments ACX 111 chipset, and that it wasn't compatible with Linux from this:
```

ubuntu@ubuntu:~ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0b:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

I was also told that I could install native Linux drivers from [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) 

Before I go ahead and install Ubuntu, though, I wanted a second opinion. Will this fix my wireless issues? It's all that's been keeping me from installing Ubuntu.

---

### Post by qrrbrrbbl on 2010-06-06
How could I install the drivers without the being connected to the Internet on my Ubuntu machine?

---


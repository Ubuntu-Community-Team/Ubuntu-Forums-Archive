---
title: "Display not recognized on new Gigabyte H370N Mobo. Resolution stuck at 1024 x 768."
date: 2018-04-22
forum: Hardware
---

### Post by cmartinkc on 2018-04-22
[COLOR=#333333][FONT=&quot]I have a new Gigabyte H370N Wifi MOBO. Using integrated graphics I can't get either Ubuntu 16 or Debian 8.1 to recognize my monitor. It shows up as "unknown" presenting a fixed resolution of 1024 x 768. My hunch is that I am missing a driver or kernel support. This MOBO uses the Intel H370 express chipset and mates with a 8th gen Core i3 Intel CPU. The onboard graphics is something I have not heard - listed in the manual as "Integrated Graphics Processor+MegaChips MCDP2800." It drives two HDMI ports ver 2 and 1.4 and a display port. Nice specs, if only it worked. Anybody know where I can score a compatible linux driver or if a fresh kernel that will rise to the occasion?[/FONT][/COLOR]

---

### Post by kurt18947 on 2018-04-22
Intel is generally good about Linux support. Have you checked their web site? Or maybe enable backports? One of the downsides of Ubuntu LTS distros (I'm assuming you're using 16.04 LTS here) is that hardware and software versions can get a little stale by the time a new LTS is due, like now. I think there's something call "Hardware Enablement" that updates hardware support but I'm not at all knowledgeable about that. You could also burn a live version of 18.04 and see if that works any better. 18.04 won't be officially released until the end of April but beta releases are available now and seem pretty stable.

---

### Post by Yellow Pasque on 2018-04-22
First, try booting with 'i915.alpha_support=1' parameter

> The onboard graphics is something I have not heard - listed in the manual as "Integrated Graphics Processor+MegaChips MCDP2800.

It's an Intel UHD 630. The MCDP2800 is just a DisplayPort to HDMI bridge, and not something users really need to concern themselves with. You should see it listed as an Intel 630 GPU if you update PCI ID database:
```
sudo update-pciids; sudo update-usbids
lspci
```

---

### Post by cmartinkc on 2018-04-24
Follow up: Seems the problem is using last years OS.  I tried Debian Testing April 16 refresh.  This worked right out of the gate.  I expect that the Ubuntu's 18.04 works also.

---

### Post by oldfred on 2018-04-24
I do not think this combination of kernels & drivers is in any distribution, yet.
But since you have very new hardware, it may be worth effort to experiment in another install and download all the updates and see if they work as advertised.

 [https://www.phoronix.com/scan.php?page=news_item&px=Intel-2018Q1-Gfx-Recipe](https://www.phoronix.com/scan.php?page=news_item&px=Intel-2018Q1-Gfx-Recipe)
The 2018Q1 Intel Graphics Stack Recipe for a recommended configuration is using the Linux 4.16 kernel, Mesa 18.0, xf86-video-intel 2.99.917, libdrm 2.4.91, libva 2.1.0, VA-API Intel Driver 2.1.0, Cairo 1.15.10, and X.Org Server 1.20 RC1.
[https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe](https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe)

---


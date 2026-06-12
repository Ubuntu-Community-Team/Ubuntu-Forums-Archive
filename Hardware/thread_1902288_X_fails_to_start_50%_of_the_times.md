---
title: "X fails to start 50% of the times"
date: 2011-12-30
forum: Hardware
---

### Post by pastoreerrante on 2011-12-30
Hi all,

I installed ubuntu 11.10 on a brand new HP pavilion dv7 6199sl. This is a dual-vga notebook:

```

daniele@HP-Pavilion:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc Whistler XT [AMD Radeon HD 6700M Series]

```The problem: X fails to start at boot 50% of the times.

Please see my Xorg.0.log for the not working scenario: [http://pastebin.com/BnJJAT3R](http://pastebin.com/BnJJAT3R) 

This is my Xorg.0.log for the working scenario: [http://pastebin.com/vFC0KGju](http://pastebin.com/vFC0KGju)

I think the problem it's related to intel video driver, since I can't see any reference to the radeon video driver (the one used by the discrete VGA). I don't understand why, but sometimes X starts without problems, sometimes X ends with "no screen found" message.

By the way the most significant errors messages are:

```

[    13.902] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.902]     compiled for 1.10.4, module version = 0.0.2
[    13.902]     ABI class: X.Org Video Driver, version 10.0
[    14.048] drmOpenDevice: node name is /dev/dri/card0
[    14.048] drmOpenDevice: open result is 12, (OK)
[    14.049] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    14.049] drmOpenDevice: node name is /dev/dri/card0
[    14.049] drmOpenDevice: open result is 12, (OK)
[    14.049] drmOpenByBusid: drmOpenMinor returns 12
[    14.049] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    14.049] drmOpenByBusid: drmGetBusid reports 
[    14.108] drmOpenDevice: node name is /dev/dri/card1
[    14.111] drmOpenByBusid: drmOpenMinor returns -1
[    14.111] drmOpenDevice: node name is /dev/dri/card2
[    14.115] drmOpenByBusid: drmOpenMinor returns -1
[    14.115] drmOpenDevice: node name is /dev/dri/card3
[    14.119] drmOpenByBusid: drmOpenMinor returns -1
[    14.119] drmOpenDevice: node name is /dev/dri/card4
[    14.122] drmOpenByBusid: drmOpenMinor returns -1
[    14.122] drmOpenDevice: node name is /dev/dri/card5
[    14.126] drmOpenByBusid: drmOpenMinor returns -1
[    14.126] drmOpenDevice: node name is /dev/dri/card6
[    14.131] drmOpenByBusid: drmOpenMinor returns -1
[    14.131] drmOpenDevice: node name is /dev/dri/card7
[    14.135] drmOpenByBusid: drmOpenMinor returns -1
[    14.135] drmOpenDevice: node name is /dev/dri/card8
[    14.139] drmOpenByBusid: drmOpenMinor returns -1
[    14.139] drmOpenDevice: node name is /dev/dri/card9
[    14.143] drmOpenByBusid: drmOpenMinor returns -1
[    14.143] drmOpenDevice: node name is /dev/dri/card10
[    14.147] drmOpenByBusid: drmOpenMinor returns -1
[    14.147] drmOpenDevice: node name is /dev/dri/card11
[    14.151] drmOpenByBusid: drmOpenMinor returns -1
[    14.151] drmOpenDevice: node name is /dev/dri/card12
[    14.155] drmOpenByBusid: drmOpenMinor returns -1
[    14.155] drmOpenDevice: node name is /dev/dri/card13
[    14.159] drmOpenByBusid: drmOpenMinor returns -1
[    14.159] drmOpenDevice: node name is /dev/dri/card14
[    14.164] drmOpenByBusid: drmOpenMinor returns -1
[    14.164] drmOpenDevice: node name is /dev/dri/card15
[    14.168] drmOpenByBusid: drmOpenMinor returns -1
[    14.168] drmOpenDevice: node name is /dev/dri/card0
[    14.168] drmOpenDevice: open result is 12, (OK)
[    14.168] drmOpenDevice: node name is /dev/dri/card0
[    14.168] drmOpenDevice: open result is 12, (OK)
[    14.168] drmGetBusid returned ''
[    14.168] (EE) intel(0): [drm] failed to set drm interface version.
[    14.168] (EE) intel(0): Failed to become DRM master.
[    14.168] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.168] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    14.168] (==) intel(0): RGB weight 888
[    14.168] (==) intel(0): Default visual is TrueColor
[    14.168] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    14.168] (--) intel(0): Chipset: "Sandybridge Mobile (GT2)"
[    14.168] (**) intel(0): Shadow buffer enabled, 2D GPU acceleration disabled.
[    14.168] (**) intel(0): Relaxed fencing disabled
[    14.168] (**) intel(0): Wait on SwapBuffers? enabled
[    14.168] (**) intel(0): Triple buffering? enabled
[    14.168] (**) intel(0): Framebuffer tiled
[    14.168] (**) intel(0): Pixmaps tiled
[    14.168] (**) intel(0): 3D buffers tiled
[    14.168] (**) intel(0): SwapBuffers wait enabled
[    14.168] (==) intel(0): video overlay key set to 0x101fe
[    14.168] (EE) intel(0): failed to get resources: Bad file descriptor
[    14.168] (II) UnloadModule: "intel"
[    14.168] (II) Unloading intel
[    14.168] (EE) Screen(s) found, but none have a usable configuration.
[    14.168] 
Fatal server error:
[    14.168] no screens found
[    14.168] 

```Thanks in advance,

Daniele

---

### Post by 2F4U on 2011-12-30
Hybrid graphics cards are still not as easy to get to work than others. You may wish to read through this documentation and see if it helps:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://askubuntu.com/questions/21455/how-to-manage-two-video-cards-on-a-laptop-ati-and-intel](http://askubuntu.com/questions/21455/how-to-manage-two-video-cards-on-a-laptop-ati-and-intel)

---

### Post by pastoreerrante on 2011-12-31
Ok, i think I fixed the problem.

I had blacklisted the radeon driver and then updated the initramfs (i want to use only the integrated vga, not the discrete one). Updating the initramfs seems to cause the problem. I re-updated it after enabling the radeon driver and now it's working.

Thank you anyway!

Daniele

---


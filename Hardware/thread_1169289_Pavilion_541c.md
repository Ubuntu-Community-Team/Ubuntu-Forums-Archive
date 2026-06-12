---
title: "Pavilion 541c"
date: 2009-05-25
forum: Hardware
---

### Post by LukeyMI on 2009-05-25
Has anybody else gotten the nvidia-glx-96 drivers working on a Pavilion 541c? I've tried searching google for some workarounds but none seem to work.

Basically as soon as I install it and reboot it either locks up the system as soon as the gdm screen shows or if it doesn't lock up I can log in and the screen becomes very artifacted and unusable.

The system has an onboard geforce2 with a max of 32 megs of shared memory. I've disabled compiz (even uninstalled it) with no effect. The nv driver seems to work fine, but looks like crap (no surprise there). The only error I seem to find in the Xorg log is about not having enough bandwidth,or something like that, for some of the resolutions. Bumping the resolution down doesn't seem to help much though as it still gets artifacted and generally very laggy.

I've also tried downloading the driver from the nvidia website and installing it manually but get the same results.

Here's my output of lspci:


```
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce AC'97 Audio Controller (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
01:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
```

Any ideas would be appreciated.

---

### Post by LukeyMI on 2009-05-27
Any ideas? I would post an xorg log but when the machine locks up I have to hit power and the xorg log goes *poof*.

---


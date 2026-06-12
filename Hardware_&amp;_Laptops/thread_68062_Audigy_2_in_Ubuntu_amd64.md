---
title: "Audigy 2 in Ubuntu amd64"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by arcticwolf_86 on 2005-09-22
Just installed Hoary. I've tried a bunch of things from other posts trying to get my Audigy 2 Value to work. It just won't work. lspci lists:

0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0045 (rev a1)
0000:02:08.0 Multimedia audio controller: Creative Labs: Unknown device 0008
0000:02:0a.0 Ethernet controller: Altima (nee Broadcom) AC9100 Gigabit Ethernet (rev 15)


this here tells me that my system doesn't recognize my Audigy 2. I've tried downloading the alsa-driver-1.0.8, but leads me nowhere...can anyone help? thanks!

sys info
Athlon64 3000+
nForce 3 250Gb
1 gig DDR333
6800GT OC
Audigy 2 Value

---


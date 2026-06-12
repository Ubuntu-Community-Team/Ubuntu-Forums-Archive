---
title: "Hardware problems on Easynote - help :S"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by madsravn on 2007-01-24
Hey there. I just convinced a friend to install ubuntu and try it out, since my own installation went almost without any pain :) But his computer fucks up a little. He has a Packard Bell EasyNote. His wireless network doesn't work and his sound has a sharp long BEEP when sound is playing. Really a pain for the ears. Anyone think they might could help? I included a lspci below. Thanks in advance


```

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d7 (rev a1)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:06:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:06:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by blackeagle83 on 2007-03-11
for resolving the sound you have to modify:
/etc/modprobe.d/alsa-base 

inserting at the end:
options snd-hda-intel model=3stack

then simply save & restart alsa server:
/etc/init.d/alsa-utils restart

if you hear the same problem try using 
options snd-hda-intel model=laptop

instead the line before

Rick

---


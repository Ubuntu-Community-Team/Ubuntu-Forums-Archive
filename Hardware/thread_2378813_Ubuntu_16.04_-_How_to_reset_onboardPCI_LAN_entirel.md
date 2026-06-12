---
title: "Ubuntu 16.04 - How to reset onboard/PCI LAN entirely (power off and back on)?"
date: 2017-11-27
forum: Hardware
---

### Post by blackaardvark on 2017-11-27
Hello there,

I'm having an issue with WoL on my PC which I made myself some time ago.  When I boot Windows before Ubuntu it's enabling some sort of WoL that I can't seem to disable no matter where I go.  It's resulting in me having no network access when I boot Ubuntu after Windows without powering down completely and hitting an actual power switch on the wall/back of the case.

Seeing as the Windows component isn't going to play ball and I can't find an answer for disabling it entirely, I'm wondering the best way to cycle this NIC that's part of my motherboard so that once I boot Ubuntu I can just do this once and I'm off.  I suspect I can do this with modprobe but i'd rather not screw things up completely...

Here's my lspci:
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 770] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
03:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)

```

Any help would be very much appreciated!

---

### Post by vidtek on 2018-08-26
boot to windows and check your power options on the network properties (device manager), there are a couple there, wol and magic packet enable.
Different names for different windows flavours.
Disabling them should fix it.

Cheers Tony.

Edit- just seen your post was a year ago-presume you fixed it and forgot to mark it solved.

---


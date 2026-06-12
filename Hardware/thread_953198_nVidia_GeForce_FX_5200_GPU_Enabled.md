---
title: "nVidia GeForce FX 5200 GPU Enabled?"
date: 2008-10-19
forum: Hardware
---

### Post by Ugeen on 2008-10-19
Hello,

In the NVIDIA X Server Settings, it looks like the Graphics Processing Unit (GPU) is enabled.

[LIST=1]
[*]How can I confirm that my GPU is enabled?


[*]If my GPU is not enabled, how do I enable it?
[/LIST]
Video Card
[LIST]
[*]PNY Verto nVidia GeForce FX 5200 PCI 256MB DDR ([Google]("http://images.google.com/images?gbv=2&hl=en&q=PNY+Verto+nVidia+GeForce+FX+5200+PCI+256MB+DDR"), [TigerDirect.ca]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2148789&CatId=319"))
[*]nVidia Driver Version:  173.14.12
[*]Resolution:  1440 x 900
[*]In a Terminal window, I typed:  sudo lshw -C display
[INDENT]
*-display UNCLAIMED
[INDENT]
description: Display controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0
[/INDENT]
*-display
[INDENT]
description: VGA compatible controller
product: NV34 [GeForce FX 5200]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/INDENT]
[/INDENT]
[/LIST]
EnvyNG
[LIST]
[*]NVIDIA:  Install the NVIDIA driver (Automatic Hardware Detection)
[/LIST]
Thank you in advance for your help.
Sincerely,
--Ugeen

---

### Post by overdrank on 2008-10-22
Moved :)

---


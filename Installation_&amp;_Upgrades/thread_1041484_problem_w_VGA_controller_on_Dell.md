---
title: "problem w/ VGA controller on Dell"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by tpd2049 on 2009-01-16
I have been trying to install ubuntu on my Dell Dimension 2300 but I can only view it in safe graphic mode. I checked the boot and it seems that the first line in the second code segment,says 'DISABLED'. that means that there is no driver allocated to it?...or the video card is not attaching to a driver? 

Here is the info on the video card:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)and 

Code:
*-display UNCLAIMED
description: VGA compatible controller
product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0

Does anyone have any suggestion on what I can do??? I'm new to ubuntu and Linux and don't have a clue...

Thanks!

---


---
title: "Black border all around lcd display."
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by Jackie999 on 2008-12-14
I have an older toshiba 1800 lappy. My monitor shows a 1" black border all around the display.  I got it fixed using the 8.04 displayconfig-gtk - unfortunately that doesn't work with 8.10.
My lshw shows:
```
*-display UNCLAIMED
                description: VGA compatible controller
                product: CyberBlade XPAi1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 82
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=8

```The specs on this display are:
Cyber Aladdin-T 128bit BLT Engine.

Any suggestions how to fix?

---

### Post by RichT70 on 2008-12-15
I've got the same problem with a Toshiba Tecra 8200. I increased the resolution to 1280x1026 by adding entries into xorg.conf - and now only have a 1" margin on the right ... still experimenting...

---


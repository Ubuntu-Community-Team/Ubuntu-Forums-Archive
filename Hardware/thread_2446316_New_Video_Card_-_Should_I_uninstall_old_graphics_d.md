---
title: "New Video Card - Should I uninstall old graphics drivers first?"
date: 2020-06-28
forum: Hardware
---

### Post by backspin on 2020-06-28
..

My new video card just arrived Radeon 5700XT.  However, I currently have proprietary drivers installed for my old video card which is a Radeon RX470.

[SIZE=3]**Should I do anything before just slamming the new video card on the motherboard?**[/SIZE]


davidc502@Ryzen-3900x:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: c7
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:187 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:f7d00000-f7d3ffff memory:c0000-dffff

---

### Post by CelticWarrior on 2020-06-28
No need and no, you weren't using proprietary drivers unless running Ubuntu form 6 years ago. Both drivers for AMD cards are now open-source and included.

---

### Post by backspin on 2020-06-28
Thanks for the info.   Is there a graphical front end these days or has that gone away?

---

### Post by Yellow Pasque on 2020-06-29
Graphical frontend for what?

---

### Post by CelticWarrior on 2020-06-29
> **Yellow Pasque said:**
> Graphical frontend for what?

I think they mean the old Catalyst GUI and that being the case no, there's isn't one I'm aware of.

---

### Post by Yellow Pasque on 2020-06-29
This is the last I heard about it: [https://www.phoronix.com/scan.php?page=news_item&px=Radeon-Settings-Possible-Open](https://www.phoronix.com/scan.php?page=news_item&px=Radeon-Settings-Possible-Open)

---


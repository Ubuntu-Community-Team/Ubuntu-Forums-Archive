---
title: "Nvidia Optimus or AMD Enduro"
date: 2012-06-19
forum: Hardware
---

### Post by robbiedobbie on 2012-06-19
Hi all,

I'm planning on buying a notebook with a dedicated graphics card. I want to run ubuntu as my main os (dualboot with windows for games though). I'm now in doubt between 2 almost identical notebooks. Both have an I7 processor with a HM77 Express chipset. The only difference is the graphics card. I have to choose between a NVIDIA GTX675m with Optimus and an AMD Radeon HD7970m with Enduro.

I know that both are not fully supported in ubuntu (or any other distro). If I understand correctly, I can use bumblebee with the nvidia for some support so that I can run individual applications on the dedicated card and with the AMD Radeon I should be able to switch between the two cards (with a X-server restart).
The bios of both laptops has no options regarding the graphics.

Which one is the best choice if I plan on using ubuntu most of the times? (I plan on programming 3d applications on both windows and ubuntu, so I can't just use the integrated intel card in ubuntu).

I'm sorry if I've made mistakes in my english, since it's not my best language ;)

Thank you in advance,
Rob

---

### Post by Yellow Pasque on 2012-06-19
Normally, Bumblebe works well, but people with the latest 6xxM Kepler-based mobile GPU's are reporting that the optirun command doesn't work, even with latest Nvidia driver: [http://www.nvnews.net/vbulletin/showthread.php?t=184421](http://www.nvnews.net/vbulletin/showthread.php?t=184421)

Note: that doesn't mean I recommend AMD hybrid, especially if you plan to use fglrx/Catalyst driver.

---

### Post by robbiedobbie on 2012-06-19
Well, the GTX675m is not a kepler based gpu (unlike the gtx 640, 650 etc), right? So that shouldn't be a problem.

EDIT: Just found out that bumblebee does NOT work with the GTX675 (yet). So that's a problem...

---

### Post by robbiedobbie on 2012-06-21
So, which one is the best to choose? Which one has the best support at the moment?

---


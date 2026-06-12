---
title: "Help - X with hybrid display"
date: 2008-09-14
forum: Hardware
---

### Post by soltanis on 2008-09-14
I have a Sony Vaio VGN-SZ430N laptop. It has a hybrid display system, which means that if I move a hardware switch to one side while booting, I can select a nVidia card to output on my display, while if I move the switch to another side, I can select a low-power Intel integrated card.

Currently, I have Ubuntu running with the nVidia card selected. This is nice for graphics performance, but it eats battery power like mad when it's disconnected from the wall jack (I literally get like...30 minutes). If I switch to the Intel chipset on boot, however, X fails to start.

I don't want to have to reconfigure X every time I decide to take this computer off AC power. How/is there a way I can write one Xorg.conf file that will work with me switching which card I'm using?

---


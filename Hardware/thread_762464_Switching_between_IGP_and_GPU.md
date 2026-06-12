---
title: "Switching between IGP and GPU"
date: 2008-04-22
forum: Hardware
---

### Post by MickeWR on 2008-04-22
Just bought a laptop, f3ka-ap014c, using vista for the moment :-& but going to install ubuntu when 8.04 is released.
F3ka has a HD2600 as main graphics but the chipset got a igp (probably x1250). There is a switch in bios between internal/pci-express.

Does anyone have any experience setting up ubuntu to boot up and have 3D acceleration for both of these cards (not at the same time)?

My tought is that I could add two graphics entries in xorg and just hope that ubuntu uses the right entry one for each of the cards.

Battery time would probably increase if i could use the IGP when on the move.

---

### Post by MickeWR on 2008-05-04
Update on the work:
Took a weekend to install all the drivers in xp properly, Ubuntu worked immediately! 
I've tested to switch to the IGP in ubuntu and it worked without modification or even a protest. CCC identifies it as x1200 series and fgl_glxgears worked with 200fps. The window with the gears flashes, I will check how hd2600 performs and see if games works with x1200.

[EDIT] Switching back worked fine and HD2600 performed 1060fps

---


---
title: "Lowering GPU clock when exiting to desktop?"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by Nesnej Trick on 2008-03-06
I sometimes go to ridiculous lengths to reduce the power usage of my rig and this time I've got my eyes on the graphics card.

Basically the idea is simple. I use the normal 2D KDE desktop environment, so the graphics card (a nVidia 7600 GS by the way) wouldn't need to run a full core and memory frequency all the time. Lowering the clock speed upon boot is achievable even with my meager scripting skills by placing a bash script using nvclock in init.d, as is raising the clock speed prior to starting Enemy Territory, Blender or Scorched 3D. However, I haven't figured out how to make the script return the core and memory frequencies to minimum once exiting aforementioned applications. Anyone care to help me out?

EDIT: As for the core, nevermind, I just figured out how to do it. However, why doesn't nvclock seem to affect the memory frequency at all?

---


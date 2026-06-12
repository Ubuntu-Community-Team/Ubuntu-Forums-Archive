---
title: "[SOLVED] compiz cube won't go transparent"
date: 2008-11-25
forum: General Help
---

### Post by shoofy on 2008-11-25
Everything about compiz is working fine for me except the transparent cube. In CCSM on the Transparent Cube tab of the Desktop Cube preferences I have both sliders set to zero and the "Transparency only on mouse rotate" box unchecked. Nothing happens if I move the sliders around. I've checked in gconf to make sure the settings are actually being reflected there and they are (I'm using the gconf config backend of ccsm). I'm using Intrepid with the fglrx drivers on an ATI X1400 card. This setup worked with transparent cube on Hardy.

Is there anything else I can try? I don't know how to get debug output from compiz to see if it's giving some kind of error.

---

### Post by shoofy on 2008-11-25
Never mind, I fixed it. I had to enable the Wallpaper plugin.

---


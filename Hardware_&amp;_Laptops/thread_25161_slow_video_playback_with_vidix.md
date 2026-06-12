---
title: "slow video playback with vidix"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by tmowerman on 2005-04-09
I have a Hp omnibook xe4500 with a 1.7 ghz processor and a 32mb ati mobility m6 graphics card.

Upon the update to hoary, xorg radeon driver stopped ati tvout from working, which i was using along with xine to watch video on my widescreen tv.  I posted a message, and someone suggested using mplayer with vidix in the console.  I even managed to find a script to create a new x display with the vesa driver and mplayer using vidix to output to tv.

So I have solved my tv out problem, except video playback is extremely slow.  I don't understand this, as my processor and graphics card are seemingly adequate.  I have tried everything mplayer reccommends, and the only way it works is with framedrop, which is unwatchable.  

I dont understand how in X, with the accelerated radeon driver, playback is fine, but with the vidix interface it is not,  I am sure I must need to set up some options correctly, can anyone help?

Tim

---

### Post by orion_114 on 2005-04-10
I found I had lots of problems with mplayer and the playback speed. I however am running a very slow machine 400 Mhz,128 MB Ram.
I found vlc player to be much better. Give it a go. It might solve your problem.

---


---
title: "OpenGL and NVIDIA card"
date: 2013-04-29
forum: Hardware
---

### Post by djpemberton on 2013-04-29
I am running Kubuntu 13.04 on a new computer. My computer has a NVIDIA GeForce GTX 650. I have tried several of the NVIDIA drivers (nvidia_304, nvidia_310, and now nvidia_313_updates). I have also tried them all with "nomodeset". With all of those arrangements leave me still without effects that require OpenGL.

glxinfo | grep '^direct rendering:'

returns "Yes" with each arrangement.

I want to get the most out of my card. Is there something that I am not doing? I have searched, but I haven't found an answer that works for me. Please Help!

---

### Post by djpemberton on 2013-04-30
OK. I do occasionally make stupid mistakes -- not commonly, but  occasionally. This was one of those times. Nothing at all, as far as I  can tell, is wrong with my card and drivers. The current driver works  fine. The Desktop Effects KDE Control Module kept telling me that  certain effects could not run because OpenGL was not on (or something  like that). The first thing to do when this happens is to click over to  the Advanced tab, and select OpenGL for the Compositing Type. Viola,  problem solved (at least occasionally). Though it is unfortunate that I  got absolutely no feedback on this, it likely turned out better that way  this time. Thanks anyway!

---


---
title: "Nvidia screen/audio output selection when notebook docked/undocked"
date: 2017-04-09
forum: Hardware
---

### Post by eclipticon2 on 2017-04-09
Hi,

I have a Dell Precision M4800 notebook with a docking station and a Dell U3415W screen connected to the docking station via Mini-DP. When the notebook is docked (and the lid is closed), I would like to use only the external screen and the DP audio output, when the notebook is undocked the built-in screen and the built-in speakers.

Since the last updapte of the NVIDIA binary driver (now version 375.39) I am experiencing all kinds of troubles: When I boot docked and with the lid closed, the notebook just beeps stupidly and never boots. When I boot it docked with the lid open, i get the login on the built-in screen, but once I am logged in, both (!) screens switch off. To get an X session for my user, I currently need to boot undocked, log in, dock, and then switch screens manually. There must be an easier way to achieve thise ...

Also, how can I make my Gnome understand that I always want to use the DP audio when docked and the built-in speaker when undocked?

I should mention that I can not use the nouveau driver, for CUDA and speed reasons (slows down display on this huge display a lot).

Thanks for any insight!

---


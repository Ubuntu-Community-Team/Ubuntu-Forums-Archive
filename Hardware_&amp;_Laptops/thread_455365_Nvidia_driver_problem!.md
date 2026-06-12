---
title: "Nvidia driver problem!"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by a12ctic on 2007-05-26
Well, yesterday I decided to install the latest nvidia drivers instead of the slightly dated ones provided by ubuntu, the install seemed to go fine and the drivers work. Today I restarted my computer and my X is gone, its trying to load both drivers. When I swich to NV, get into X and renable the Ubuntu provided drivers it gives me the same error. So does anyone have an idea of how to uninstall the Nvidia drivers and allow me to just use the Ubuntu provided drivers again?

---

### Post by andrebrait on 2007-05-26
have you tried to edit xorg.conf and use nv driver instead of nvidia?
after that, try to uninstall the nvidia drivers with synaptic/apt-get
if you're in text mode, try this

> 
sudo apt-get remove nvidia-glx


or nvidia-glx-new...

---

### Post by a12ctic on 2007-05-26
Yeah, I tried that, it doesnt work, I think theres a bit more wrong than that, the new drivers are the ones that arent working correctly, thats what I need to get rid of.

---


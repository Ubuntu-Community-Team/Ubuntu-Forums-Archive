---
title: "I have to run xfix in recovery mode to use my computer."
date: 2008-12-22
forum: Hardware
---

### Post by jwdresser on 2008-12-22
When I turn on my computer and the first grub entry loads x windows can't start. If I enter recovery mode and run xfix then resume normal booting x works. Once all booted up the back up xorg.conf file that xfix creates is exactly the same as xorg.conf. 

Does anybody know whats going on here and how I can fix it?

---

### Post by Mewshi on 2008-12-22
Is it doing it still?  Also, try running diff between the files.

---

### Post by DieB on 2008-12-22
with 8.04 we did get an x.org-server reduces the entries inside of xorg.conf to almost zero (at least that was their goal).

pls have a look in hardware&drivers if there is a driver for your video-card or type lspci to see if u either run an nvidia or ati/amd graphic card, the interesting line says "VGA compliant ....".

---


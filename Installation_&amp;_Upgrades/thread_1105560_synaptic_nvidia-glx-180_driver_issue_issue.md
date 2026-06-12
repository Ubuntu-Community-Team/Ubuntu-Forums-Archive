---
title: "synaptic nvidia-glx-180 driver issue issue"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by betx983 on 2009-03-24
I get the same result if I use the 177 or 180 driver. New to Ubuntu need help! Using synaptic I select the 180 driver it grabs the rest of the associated files. They install. No reboot is prompted, i reboot. Now all i boot to is the ctrl-alt-F1 screen with [email]username@computername:~$.....ctrl[/email]-alt-F7 takes toggles to a blinking cursor. Please guide me as I learn ubuntu...keep KISS in mind would help me. Maybe running in SLI is the cause of my problems. Intrepid Hardware: EVGA 780i, 8800GTS 512 SLI...

---

### Post by norwoods on 2009-03-24
you could try running:
 sudo nvidia-xconfig --sli=on
there is an nvidia README at:
[ftp://download.nvidia.com/XFree86/Linux-x86/180.41/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.41/README/index.html)

---

### Post by betx983 on 2009-03-24
thank you..i will give that a try and read the README

---

### Post by betx983 on 2009-03-26
i tried your suggestion to no avail. working through the README now...any other advice is appreciated.

---


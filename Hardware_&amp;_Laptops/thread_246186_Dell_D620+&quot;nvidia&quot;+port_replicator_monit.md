---
title: "Dell D620+&quot;nvidia&quot;+port replicator monitor"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by sheino on 2006-08-28
Here's the setup:

Dell D620 docked in port replicator
Dell 2005 FPW (20in wide screen digital display)
Nvidia Quattro NVS 110M

Above setup works fine using "nv" driver configured in xorg.conf.
apt-get installed nvidia drivers and modified xorg.conf to "nvidia".
Now get around 2200fps w/ glxgears(sp) with LCD laptop monitor
When docked using new nvidia driver I cannot get anything on external monitor. If I open the lid to the laptop I can see that the display has now been redirected to the laptop LCD screen instead of the external monitor.

Key combinations (lcd/crt) scramble the video on both screens. 

Switch back to "nv" driver in xorg.conf and all is well. 

Any help surely appreciated.

Darin....

---


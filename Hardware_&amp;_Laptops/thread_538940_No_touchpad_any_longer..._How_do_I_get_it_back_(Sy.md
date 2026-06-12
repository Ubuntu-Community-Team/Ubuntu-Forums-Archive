---
title: "No touchpad any longer... How do I get it back? (Synaptics, HP Laptop)"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by motin on 2007-08-30
My touchpad has been working great, but after having installed Gutsy on a separate partition (to check if suspend/resume works in Gutsy) and suspended/resumed the computer the touchpad won't initialize. Doesn't matter if I boot into Gutsy or Feisty...

This is all I get nowadays (from /var/log/Xorg.0.log), that reminds me of the good old days without the need of a USB mouse:

```
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 17 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "true"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
```

Hrrm how can I get it back in business you think?

---

### Post by motin on 2007-11-07
Now I have fully upgraded to Gutsy and once again the touchpad fell dead after an attempt to suspend/hibernate!

What package should I report this buggy behavior against? The kernel?

Thanks

---

### Post by pekka72 on 2007-11-28
Same problem here. My touchpad is dead since the Gutsy upgrade. I have an acer travelmate 3220. I'm happy to provide any additional information. I'm completely stuck.

---


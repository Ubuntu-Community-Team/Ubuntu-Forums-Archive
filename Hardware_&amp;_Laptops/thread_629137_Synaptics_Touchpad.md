---
title: "Synaptics Touchpad"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by thetimekeeper on 2007-12-02
I don't think I actually have a Synaptics touchpad on my device, as I get these errors in my /var/log/Xorg.0.log:

(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizEdgeScroll" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

Is there anyway to prevent the module from loading, and may speed up my boot or something? I tried commenting out those lines in my Xorg.conf but it cried foul.

---


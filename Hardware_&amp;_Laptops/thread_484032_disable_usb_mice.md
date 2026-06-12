---
title: "disable usb mice"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by binary.koala on 2007-06-25
hi there, 
i got rather nontrivial problem here, i need to unbind usb mice from common "mouse" device. 
however, event devices in /dev/input/events shall remain, as the mice are used by another program (PD), they are basically sensors.
for now (default feisty install) all usb mice are bind to /dev/input/mice which is quite normal. the weird thing that i figured out is that all of them are bind to /dev/psaux too!
I still need /dev/psaux as my system mouse is ps/2.

have anyone got any idea how to split the mice, or not to bind them all to one in the first place?
i repeat, all devices shall remain, just that "system" mouse have to bind to ps/2 one.

thanks.

---


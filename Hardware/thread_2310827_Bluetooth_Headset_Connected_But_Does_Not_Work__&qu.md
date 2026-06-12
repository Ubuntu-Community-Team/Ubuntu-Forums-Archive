---
title: "Bluetooth Headset Connected But Does Not Work / &quot;module-bluetooth-discover&quot; fails"
date: 2016-01-22
forum: Hardware
---

### Post by Tohunga on 2016-01-22
I have a bluetooth headset that connects, but does not work.
It shows up in devices and in Sound Settings. However, it cannot be selected in Sound Settings. 

It is also shown as connected in Bluetooth Manager, but attempts there to switch to the Headset audio profile give me a "Failed to change profile to headset_head_unit" message.

I am vaguely aware that it may be linked to the module "module-bluetooth-discover", but "pactl load-module module-bluetooth-discover" gives me a "Module initialization failed"
(this is true for all modules I attempt to load including "module-jack-sink" and  "module-jack-source")

Any help would be very greatly appreciated.

---


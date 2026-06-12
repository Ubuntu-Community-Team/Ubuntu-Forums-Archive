---
title: "ultra-sensitive touchpad, cursor moves by itself"
date: 2012-03-21
forum: Hardware
---

### Post by jssilva on 2012-03-21
Hello,

I had to disable tapping because the simple fact of moving the cursor produces tapping all over.

Furthermore, if I place my finger still about half inch from the touchpad bottom, the pointer starts moving down slowly.

That's on an Asus N53SN laptop running oneiric fully updated and this started recently. My xorg log says it detects an ETPS/2 elantech touchpad and load the synaptic driver but then it gives an error:

```
[    36.729] (EE) Query no Synaptics: 6003C8
[    36.729] (--) ETPS/2 Elantech Touchpad: no supported touchpad found
[    36.729] (EE) ETPS/2 Elantech Touchpad Unable to query/initialize Synaptics
hardware.
[    36.729] (EE) PreInit returned 11 for "ETPS/2 Elantech Touchpad"
[    36.729] (II) UnloadModule: "synaptics"
[    36.729] (II) Unloading synaptics

```I've already tried all sorts of combinations on gpointing-devices-settings: palm detection, speed, acceleration... to no avail.

Any help, please?

---


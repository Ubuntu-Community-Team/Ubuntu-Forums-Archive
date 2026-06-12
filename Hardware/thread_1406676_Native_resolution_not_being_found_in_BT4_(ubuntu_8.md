---
title: "Native resolution not being found in BT4 (ubuntu 8.10)"
date: 2010-02-14
forum: Hardware
---

### Post by CharlesA on 2010-02-14
I'm trying to get this working and apparently the only resolution that works is 800x600 (display is 1024x600). The laptop is an Acer Aspire One 532h-2268. Specs of the netbook are [here]("http://support.acer.com/acerpanam/netbook/2010/Acer/Aspire/AspireOneAO532h/AspireOneAO532hsp2.shtml").

Is there a way to force the 1024x600 resolution? I tried editing the xorg.conf file but that didn't work.

Any ideas on this?

Thanks.

---

### Post by 2hot6ft2 on 2010-02-14
Have you tried installing the restricted drivers for your graphics card?
You'll need to go into
Kmenu > System > Synaptic then click on Settings > Sources and enable restricted drivers.
Then go to the Kmenu > System > Add remove programs > Hardware Drivers
select the one for kde since there will be 2 of them install it and go to
the Kmenu > System > Hardware Drivers
I think that's where everything is from memory. See if there are any available to install.

---

### Post by CharlesA on 2010-02-14
Thanks! I'll give it a shot when I get home.

EDIT: Looks like BT doesn't have a Hardware Drivers menu listed. I'll poke around and see if I can find it.

Looks like the only "hardware drivers" I've found listed are in gnome add/remove software applet.

BT4 is running KDE, will that cause a problem?

---

### Post by CharlesA on 2010-02-15
Tried installing hardware drivers on BT4, but that didn't make any difference. Editing xorg.conf didn't make any difference either, all I get is "no screens found" until I run fixvesa.

The annoying part is that Ubuntu 9.10 Desktop/netbook remix work fine, but those are more updated versions.

---


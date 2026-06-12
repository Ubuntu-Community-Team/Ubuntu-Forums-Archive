---
title: "Audigy 2 NX USB always on mute!"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by reflection on 2005-04-20
Hi guys,
Sorry to post about an old issue, but all the suggestions made previously didn't work for me  ](*,) 
I have a laptop with a AC97 integrated soundchip. I have my Audigy 2 NX USB plugged in ok, /proc/asound/cards lists it. I have tried to disable the mainboard soundcard renaming the relevand .ko modules, and even if the NX is listed as the only sound card, it's still with the mute light on, as if it's not loaded. Unfortuanely I can't find a way to disable the AC97 from bios to be more sure about its status.

Can anyone please help?
Thanks

---

### Post by diebels on 2005-04-20
You see it in gnome-volume-control? Any unmuting buttons there? If the internal card has no module with the correct name, it will be disabled for sure.

---

### Post by reflection on 2005-04-21
Checked it: it is actually there and unmuted. 
About the integrated soundcard, what I meant is that even disabling it the USB soundcard wasn't going anywhere. Many other posts I found on other forums suggested to do so, and even doing so didn't help.

---

### Post by diebels on 2005-04-21
explore all the menus in gnome-volume-control. I normally change the device in the file menu to alsa-mixer. It's oss-mixer by default

---


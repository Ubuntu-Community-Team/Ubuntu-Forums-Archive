---
title: "USB Audio - sound effects but no music"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by hndrcks on 2005-03-01
I just installed Hoary on a PC with an external USB sound device (YAMAHA RP-U100). The funny thing: sound effects work fine (drums at login, the little 'plonk' when you select an item). However, when I try to add a volume control to the taskbar, or try to open the Volume Control in the menu. I get:

"No volume control elements and/or devices found."

If I open Rythymbox and try to play a file I get 

"ALSA device "default" is already in use by another program."

If I go into devices, the Yamaha shows up fine. The usb_snd_audio module is loading too (I put it in /etc/modules just in case - no help).

An FYI - this PC had Warty running on it before and the Yamaha thing worked fine. I installed Hoary - install NOT upgrade - but didn't format the /home partition. Is there a relic from Warty in /home that is perhaps causing the problem?

---


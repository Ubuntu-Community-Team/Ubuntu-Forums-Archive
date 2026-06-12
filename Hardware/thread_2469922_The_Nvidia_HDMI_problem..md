---
title: "The Nvidia HDMI problem."
date: 2021-12-13
forum: Hardware
---

### Post by Tadaen_Sylvermane on 2021-12-13
I've installed an older Nvidia GT730 into a machine. This machine is connected to a 55" Samsung TV. We use it for Zoom meetings and I stream some Steam games to it.

The issue is if the computer is started with the TV off then the computer can't seem to see the audio part of the HDMI. Apparently this is a documented problem and I've been trying to work around it. I can connect a sound bar or some nice speakers to it but if I can find a way to rescan when it detects the tv or something then I can avoid that and just rely on the HDMI sound on the TV.

Some of my research has involved it losing or not being able to find the EDID of the tv. Is there a way to scan for that or trigger it every so often without killing an active sound or video transmission? Something that could be scripted and just run in the background the whole time?

---

### Post by pqwoerituytrueiwoq on 2021-12-15
once you get the tv on are you not able to set the audio in sound settings?

when i was using a tv for a monitor i mounted a ir led on my desk and had a button hooked up to my raspberry pi so when i  pressed it it would use irsend to simulate the remote's power button and then turn the computer on via WOL, also has it setup to put the system into sleep mode and turn the tv

i do seem to recall patching the edid (you just need to save it to a file using some program and patching it with idk what tool) and loading it via xorg.conf to make it think it was DVI so i could use analog audio input so i could use the audio feed with multiple sources. i think i was running ubuntu 10.04 back then so i do not recall  the details from back then

---

### Post by Tadaen_Sylvermane on 2021-12-16
hasn't worked thus far that way. has always required a reboot. if the tv is on first though it works every time.

what you said though about patching the edid and saving it gave me something to google for.

[https://kodi.wiki/view/Archive:Creating_and_using_edid.bin_via_xorg.conf](https://kodi.wiki/view/Archive:Creating_and_using_edid.bin_via_xorg.conf)

I'll give this a go and see what happens. thanks much. will report back.

---


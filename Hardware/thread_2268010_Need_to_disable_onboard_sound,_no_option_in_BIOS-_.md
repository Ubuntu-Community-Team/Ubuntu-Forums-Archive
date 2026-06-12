---
title: "Need to disable onboard sound, no option in BIOS- Sony Vaio"
date: 2015-03-05
forum: Hardware
---

### Post by fallenstardust on 2015-03-05
[COLOR=#333333][FONT=UbuntuRegular]I have a bad interference problem with audio, from the second I boot my laptop, before I select my OS. It is only a problem through my PA system, when connected directly or indirectly (via the tv through HDMI and audio out the TV to PA; or directly through the headphone port), but other devices (phone, iPod) work fine through the same cable to the PA system. Also, laptop to TV only via HDMI (not out to PA) works fine. It is most bizarre, it only occurs when the laptop is connected to the PA, and only since today. It was fine yesterday.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So, I want to disable my soundcard in Ubuntu to see if I can get clean sound out the HDMI to TV with TV connected to PA, since it's such a weird thing to occur and I'm out of ideas. It's a Sony Vaio and there is no option for disabling anything in the BIOS, I've searched it thoroughly. I figure that sound should still work through HDMI without a sound card or am I mistaken?[/FONT][/COLOR]

[LIST]
[*]Ubuntu 12.10 Gnome

[*]00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)

[*]Sony Vaio EPCEH Laptop
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]The PA system is my stereo.

I have searched thoroughly for an idea of how to disable the soundcard, but all anything says is "do it through the bios", which there isn't an option for.[/FONT][/COLOR]

---

### Post by kerry_s on 2015-03-05
if you disable the card, you'll get no sound at all.
go in to settings-> sound & change the output to what you need
there should be a shortcut to settings in the volume icon menu.

---

### Post by fallenstardust on 2015-03-05
> **kerry_s said:**
> if you disable the card, you'll get no sound at all.
go in to settings-> sound & change the output to what you need
there should be a shortcut to settings in the volume icon menu.


Hi,

thanks but changing the sound output doesn't change the interference that starts on boot. I was looking to disable the device to test the HDMI only but it seems that wouldn't have worked anyway.


However, if anyone ever has the same problem about random interference, check your power supply. It turns out it was my dc 12v - 19.5v car charger power transformer that was causing the interference. I live on a boat, so dc power for the laptop is better as I don't have to turn on my ac inverter all the time. All is well now, I just switch to ac when the inverter and PA is turned on.
 :guitar:

---

### Post by Yellow Pasque on 2015-03-05
Please mark the thread solved (thread tools menu above first post). 
For reference, you may have been able to blacklist the corresponding kernel module (it would be easy just to blacklist snd-hda-intel, but that probably would have prevented HDMI audio as well).

---


---
title: "No sound through HDMI (ATI HD6450)"
date: 2013-06-25
forum: Hardware
---

### Post by audigex on 2013-06-25
Hi

I've just got myself a HP Microserver as a new home server, HTPC and first foray into the world of permanent linux (I use CentOS at work, and have dabbled with various distro's in Virtual Machines) but this is the first time I've had to concern myself with my own hardware.

So, obviously, it's gone wrong.

I've installed a clean install of Ubuntu. My system is a basic HP Microserver N54L (2.2GHz dual core AMD CPU - I think it's an Athlon, 2GB PC3-10600) with an ATI HD6450 outputting over HDMI to an AV reciever, which strips the sound off and plays it, while it sends the picture to my monitor. Nothing too other-world.

So I get Ubuntu installed, no problems. Screen resolution and picture are fine, everything works nicely... until I test the sound. Nothing plays, so I checked my sound settings. The only playback device present is "Dummy output". Realising I hadn't installed the ATI driver I did so. I now see the Catalyst Control Panel in my programs.
[ATTACH=CONFIG]244164[/ATTACH]

So i checked aplay -l, with the following output:
[ATTACH=CONFIG]244165[/ATTACH]
This seems to recognise the HDMI?

And then tried the following (top half command, bottom half output) which seems to show that the system knows it has an HD6400 series card installed.
[ATTACH=CONFIG]244166[/ATTACH]

So I tried looking in Alsamixer, which gave the following - the part which interests me is the S/PDIF [Off] which suggests, obviously enough, that the digital output is switched off.
[ATTACH=CONFIG]244167[/ATTACH]

Which hit the end of my googling ability. Does anyone have any idea what the issue could be? Is it as simple as me needing to turn the S/PDIF on somewhere? Please note that I don't have an analogue out option, as the Microserver doesn't come with any audio capabilities.

EDIT: I've realised that the S/PDIF out was muted in alsamixer. I've selected the card and pressed "m" to unmute, which now leaves me in the exact same situation as above, except that the Item: S/PDIF [Off] now just says Item: S/PDIF.

Any advice appreciated
Thanks

---

### Post by audigex on 2013-06-25
SOLVED: This appears to be an issue in 13.04. By installing the proprietary drivers in 12.04 LTS, I've resolved the issue.

---


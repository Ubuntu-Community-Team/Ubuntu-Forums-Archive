---
title: "Sound Blaster Live acting friggin' weird"
date: 2005-11-20
forum: General Help
---

### Post by Mosey on 2005-11-20
So after a few hours of following a handful of how-to's on how to get a SB Live 24-bit card to work I came across a few solutions and a few more problems. Now I must ask for help.

I've disabled my onboard sound in the BIOS
I've added my card to the module list

Still no sound...so following the advice of numerous other help guides I began tinkering around in alsamixer to see if that was the issue

I muted 'SPDIF out'

ctrl-alt-backspace

PRESTO! System sounds and mp3 playback in XMMS are GO!

But now I can't control my volume level from the gnome-panel. I have to go into alsa mixer...also, my system volume meter is still reading nothing.

When I go into Multimedia Systems Selector and fool about with the tests

ALSA and ESD test fine.
But Artsd and OSS spout of this error: "Failed to construct test pipeline for '**** Sound Daemon'"

Something is still not quite right.

I'd really love to resolve this soundcard issue. I had to ditch my onboard sound because it's "too new" and wasn't supported by Ubuntu. I purchased a soundcard and I'm still having troubles.

...figs.

---

### Post by Mosey on 2005-11-20
bump

---

### Post by Mosey on 2005-11-20
bump bump

---

### Post by Vlammetje on 2005-11-30
I have all the same problems, no sound control on my gnome panel and it won't stick whenever I try to reattach it, also only esd and alsa seem to work, also I can only get stereo (at best) or mucho static (at worst) from my 5.1. system.... any tips??:(

---


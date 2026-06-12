---
title: "Realtek ALC655 stereo recording breaks after 9.04"
date: 2011-01-13
forum: Hardware
---

### Post by Effcook on 2011-01-13
I'm having trouble getting a Via C7VCM motherboard to record audio
on Ubuntu 10.10 and 10.04 (Desktop).  Both behave the same way.

I set up the sound card with gnome-alsamixer and checked the
pulse audio settings with pavucontrol.  I'm using Audacity's
input meter (enabled) to monitor input activity.  I also tried
the command line arecord utility and had the same problem.

The sound chip is a Realtek ALC655 rev 0.
I can get meter activity from the mic (mono), but when I select Aux
(stereo), I can monitor the aux input sound but it won't record
or show up on the meter.
Same thing goes for the CD (stereo) audio input, monitor works but
record doesn't.
I set the capture level up and enabled recording on capture and aux.

For fun, I tried a test install of Ubuntu 9,04 on the same motherboard.
With 9.04, stereo recording works fine.  I was careful to set all of the
mixer levels/flags to similar values on the three different OS levels.

This seems like a driver issue to me, does anyone know what's going on?
:confused:

---


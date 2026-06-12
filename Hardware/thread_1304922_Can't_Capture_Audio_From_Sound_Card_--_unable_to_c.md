---
title: "Can't Capture Audio From Sound Card -- unable to change option in alsamixer"
date: 2009-10-29
forum: Hardware
---

### Post by Khufucius on 2009-10-29
I've been searching for a few days now, but haven't found anything that works for my situation.  I'm running a Toshiba Satellite L305-S5957.  lspci shows my sound card as:

Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

**I've been trying to rip some audio from an .mp4 video**.  First I made sure that my alsamixer settings were what they should be.  In the alsamixer Capture-menu, the capture volume is at a normal level, unmuted, but <input-so> is permanently set to "mic."  I can't change the setting from "mic" to anything else.  Could that be my problem?

One more alsamixer thing: the <CAPTUR> text, along with the L/R text above it, is colored RED.  I'm not sure if this means it's muted, but I've tried unmuting it with m/M, and that doesn't seem to have any effect.

I've tried using ```
arecord
``` I've tried using ```
mplayer -dumpaudio
```, I've tried using avidemux to rip the stream (avidemux seems to have trouble getting sound from the .mp4, and the stream it saves seems to be corrupted -- I can't open it with any audio programs).

My LAME libraries are up to date, so I don't think that's it.

I've also used to GUI volume control, attempting to playback with every listed device.  Under the "recording" tab, the only selectable input is "mic," just like in alsamixer.

[B]
Is it possibly that I simply can't monitor/capture directly from my sound card?[/B]

I've got a bad case of the newbs, so I apologize -- I'm not entirely sure if I can dismiss this as being purely a software thing.

Thanks in advance,

-Khufu

---

### Post by Khufucius on 2009-11-20
I'm starting to think this is a hardware issue.  Reformatted the hard drive and installed a clean version of 9.10, and it's still the same.  I'm just going to pretend it's my sound card for now...at some point I'll try splicing a new one into this computer to see if it solves the problem.

I'll post here when that happens.

-Khufu

---


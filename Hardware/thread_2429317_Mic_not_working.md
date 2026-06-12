---
title: "Mic not working"
date: 2019-10-16
forum: Hardware
---

### Post by Dy1anW on 2019-10-16
Hi,

I can't seem to get my mic to work on my laptop. From sound settings/pavucontrol I can see it shows an internal mic, it's switched on, input volume is all the way up, but I get no orange bars. The same goes for when I use earphones with a mic (with a single TRRS jack).

Interestingly when I look in alsamixer I don't even have an option for mic volume (???).

Audio output works just fine, so no issues on that side.

Also the built in camera works fine too; it's just the mic that's not playing along.

I'm on Ubuntu 18.04, and my laptop is an Acer Swift 5.

---

### Post by CatKiller on 2019-10-16
> **Dy1anW said:**
> Interestingly when I look in alsamixer I don't even have an option for mic volume (???).

The default alsamixer display is just playback channels. F6 lets you pick the sound device you're interested in, and F3/F4/F5 toggle whether it's showing playback/capture/all channels.

---

### Post by Dy1anW on 2019-10-17
Okay, I've finally got it working... sort of.

I tried the following options in /etc/modprobe.d/alsa-base.conf (not all at the same time).

> 
options snd-hda-intel model=alc255-acer
options snd-hda-intel model=dell-headset-multi
options snd-hda-intel model=headset-mic


alc255-acer should have been the one that should work since I'm using the ALC255 codec and on an Acer laptop. Nope, nothing.
headset-mic was a no go.
dell-headset-multi removed the built in mic from input devices, but the built in mic and headset mic both show up as soon as I plug in a headset, and it works fine at least. I can't test audio output (from settings), but it works.

Eh... Good enough for government work, as they say. I'm not going to try and 'fix' it any further.

---

### Post by mfry on 2020-03-19
Hi Dy1anW,

I'm running into similar problems and have read posts similar to this (mostly consisting of "set: options snd-hda-intel model=some_model_name").  You listed a number of model names that you checked.  Is there a list of model names that I could look up and try? 

I'm trying to get my internal mic for the Dell Precision M6800 working on Ubuntu 18.04 (Intel HDA PCH sound card with Realtek ALC3226 codec).

---


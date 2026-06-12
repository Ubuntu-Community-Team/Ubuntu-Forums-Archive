---
title: "Sound Problem"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by Dr Zolygon on 2007-10-26
I am having some trouble with my sound in Ubuntu 7.10. My sound card is a x-fi sound blaster extreme audio.  When I run the test in the sound preferences it works fine. But I cannot get it to work with anything else. The speaker icon in the panel has a little "x" on it but when I try to double-click it I get the following error.

"No volume control GStreamer plugins and/or devices found."

I have tried reinstalling alsa a few times with no success.

Also in the sound preferences, there is nothing listed under default mixer tracks(nothing in the drop down menu for devices or in the box below).

Any help is appreciated.

---

### Post by Dr Zolygon on 2007-11-03
Bump

---

### Post by Dr Zolygon on 2007-11-04
Here is an update for the things i have tried.

I have downloaded, compiled and installed the latest alsa driver 1.0.15 and upon reboot found that I still do not have sound. I still get the error: "No volume control GStreamer plugins and/or devices found." and nothing is listed under default mixer tracks in sound preferences. I tried using the command "alsamixer" and it turned up the error: "alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference"

I have no idea what to do and I cannot find any guides online that work for me.

Any help is appreciated.

---

### Post by Dr Zolygon on 2007-11-05
bump

---


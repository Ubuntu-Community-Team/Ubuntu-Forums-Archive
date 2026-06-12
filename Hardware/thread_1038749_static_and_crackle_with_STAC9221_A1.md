---
title: "static and crackle with STAC9221 A1"
date: 2009-01-13
forum: Hardware
---

### Post by werries on 2009-01-13
I have a Sigmatel STAC9221 A1 HD audio.
ALSA classifies it as hda-intel.

I use PulseAudio, and that passes to ALSA.
Whenever i do a sound test, i hear a pop, and the high pitched noise that tests it. but there is also a static in the background.

And besides that, i get a bunch of static in flash, and a little in mp3 playback.

I'm no audiophile, but its annoying. I've tried to compile my own alsa drivers, 1.0.18a instead of 1.0.17 offered by intrepid, but no change.
Why is it static-y? :( help!

---

### Post by HittingSmoke on 2009-01-13
> **werries said:**
> I have a Sigmatel STAC9221 A1 HD audio.
ALSA classifies it as hda-intel.

I use PulseAudio, and that passes to ALSA.
Whenever i do a sound test, i hear a pop, and the high pitched noise that tests it. but there is also a static in the background.

And besides that, i get a bunch of static in flash, and a little in mp3 playback.

I'm no audiophile, but its annoying. I've tried to compile my own alsa drivers, 1.0.18a instead of 1.0.17 offered by intrepid, but no change.
Why is it static-y? :( help!

Some boards create electrical noise with the onboard audio. I had this problem on Windows very bad with my Realtek onboard audio.

Strangely enough, after I switched to Ubuntu it was much less noticeable.

Turned out that I could eliminate it by turning down PCM. It will make all your sounds a tad quieter, but help wonders with the static noise.

---


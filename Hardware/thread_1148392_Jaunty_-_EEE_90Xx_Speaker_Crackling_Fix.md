---
title: "Jaunty - EEE 90Xx Speaker Crackling Fix"
date: 2009-05-04
forum: Hardware
---

### Post by beastrace91 on 2009-05-04
So Jaunty 9.04 NBR has the same issue with the speakers displaying a "crackling" sound when you mute them/put the volume to a low level with the default settings that EasyPeasy has...

Here is the quick fix so at least muting works:
1. Go to Preferences > Sound.

In order, make the boxes say this:
Autodetect
Autodetect
Autodetect
HDA Intel ALC269 Analog (ALSA)
Playback: ALSA PCM on front 0 (ALC269 Analog) via DMA (PulseAudio Mixer)
Make sure "Master" in the box below is highlighted.

2. Right-click the volume icon on the Panel, select Open Volume Control
In Device, select HDA Intel (ALSA Mixer)
Make sure the sliders for PCM and LineOut are at maximum.

~Jeff

---

### Post by jan.hana on 2009-05-06
> **beastrace91 said:**
> So Jaunty 9.04 NBR has the same issue with the speakers displaying a "crackling" sound when you mute them/put the volume to a low level with the default settings that EasyPeasy has...

Here is the quick fix so at least muting works:
1. Go to Preferences > Sound.

In order, make the boxes say this:
Autodetect
Autodetect
Autodetect
HDA Intel ALC269 Analog (ALSA)
Playback: ALSA PCM on front 0 (ALC269 Analog) via DMA (PulseAudio Mixer)
Make sure "Master" in the box below is highlighted.

2. Right-click the volume icon on the Panel, select Open Volume Control
In Device, select HDA Intel (ALSA Mixer)
Make sure the sliders for PCM and LineOut are at maximum.

~Jeff

Thanks, works fine with 9.04 on Eee 1000HE.

---

### Post by paloberjot101 on 2010-01-30
holy j'molies! it worked! i was stuck on this for hours! i have an acer extensa 4420 with realtek audio drivers. i had thought it was a driver issue. it was drivin me nuts! you're a genius Jeff

---

### Post by beastrace91 on 2010-01-30
Very good, at any rate I just copied these instructions from elsewhere - but Ubuntu forums always hits near the top of Google searches so when I find a good HOWTO I repost it here :)

Cheers,
~Jeff

---


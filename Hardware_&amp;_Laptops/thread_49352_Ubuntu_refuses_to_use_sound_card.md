---
title: "Ubuntu refuses to use sound card"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by JesterMania on 2005-07-16
I have 2 soundcards installed in my system (built-in Realtek and a PCI CMedia - needed the gameport on that card).  My goal is to make GNOME use the built-in Realtek card, but it insists on using the CMedia card instead.  After some searching, people seemed to recommend using ALSA instead of OSS and as such, I followed some instructions I found and created a ~/.asoundrc file with:

```

pcm.!default
{
        type hw
        card 1
}

ctl.!default
{
        type hw
        card 1
}

```

since in the volume control it showed this:

0: C-Media PCI (OSS Mixer)
1: Realtek ALC650E (OSS Mixer)
2: C-Media PCI CMI8738 (Alsa Mixer)
3: VIA 8235 (Alsa Mixer)

so I assumed the 2nd Alsa device (VIA 8235) represents my Realtek card under ALSA.  This method works great under applications where I can specify what device to use (alsasrc & alsasink) and I get sound in XINE, amaroK, Rhythmnbox, etc.  However, GNOME itself still cannot play sound from my Realtek card, not even after I've selected 3: VIA 8235 (Alsa Mixer) under volume control.

Does anyone know how I can get GNOME itself to use VIA8235?   Any help is appreciated.

---


---
title: "Acer TimelineX 3830t sound stopped working"
date: 2012-03-06
forum: Hardware
---

### Post by afamiglietti on 2012-03-06
Hey everybody, 

I'm having an audio problem with my Acer timelinex... things were working fine at first, but then the sound stopped working. I was able to fix that by running "alsa force-reload," but today THAT stopped fixing the problem. Does anyone know what is going on here? Here is the result of running "alsa force-reload." 


```
Unloading ALSA sound driver modules: snd-hda-intel snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-hdmi snd-hda-codec-conexant snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-hda-codec-hdmi snd-hda-codec-conexant snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-hdmi snd-hda-codec-conexant snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
```

---


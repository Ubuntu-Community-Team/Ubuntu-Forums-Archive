---
title: "Sound."
date: 2013-12-27
forum: Hardware
---

### Post by Andrew_Lucas on 2013-12-27
Hi all,

I've got *no* sound at all (Xubuntu 13.10, Creative Sound Blaster LS, 5.1 speaker set up). Xubuntu doesn't seem to come with any way of configuring it, so I installed the 'xfce4-mixer' package, but it hasn't been much use.

Since there was initially no icon, what I've done is purged the indicator-sound package, and some of the Pulse packages, and instead installed volti. ASLA is still installed also.

What I suspect is happening is that the 'master' channel is the HDMI on the video card, or else the onboard sound card. Given a lack of a suitable mixer, I don't currently have a way of testing this. Ideally, to avoid future problems, a solution would involve disabling those unused channels.

Thanks!

---

### Post by JDorfler on 2013-12-29
Have you tried ```
alsamixer
```

---

### Post by Bucky Ball on 2013-12-29
Apps>Multimedia>Pulseaudio Volume Control.

Volti??? Why? You are starting to complicate things. Definitely not standard, never heard of it and can't find any details. Go back, wrong way. Also, randomly removing bits of Pulseaudio is a bad idea and has possibly made things more complicated again. I would advice reinstalling Pulseaudio and getting things back to how they were.  

Open Pulseaudio Volume Control, click the 'playback' tab. Get a stream going (audio from VLC, Youtube, wherever) and you should see that stream in the tab. Is it indicating there is sound in the volume indicator? If so, try the 'output' tab and see if there is anything muted there or if it is set to the correct device.

PS: Yes, just found details for Volti. Is GTK. You don't need that. Did it install a heap of dependencies???

---


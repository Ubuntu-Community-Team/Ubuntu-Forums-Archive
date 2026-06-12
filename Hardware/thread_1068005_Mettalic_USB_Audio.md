---
title: "Mettalic USB Audio"
date: 2009-02-12
forum: Hardware
---

### Post by Bob3Rocks on 2009-02-12
I recently got a new Toshiba laptop with with AMD Athlon x2 64 bit processor, 3gig ram, SATA drives. USB audio just doesn't cut in in Vista, even after hours of tweaking. Naturally I installed a variety of Linux distros to try to get some decent audio working. I am currently running ubuntu 8.04 studio 32 bit, with a M-Audio Fast Track for recording audio. I got realtime low latency working nicely with Ardour, both input and output at 5ms through the Fast Track.

I am partial to another audio application called Reaper. Installed Wine and Wineasio and got it up and running.

With Reaper, playback sounds great. But audio capture at low latencies sounds metallic, like a robotic voice effect. I am using the most recent wine and wineasio. I have tried two different RT kernels with the same effect. I have tried all kinds of different jack settings. 

Even though the sound is crappy, there are no XRUNs in Jack.

Has anyone had luck with this setup?

---

### Post by Bob3Rocks on 2009-02-12
After much digging I found another thread which states I need to use audio input hw:1,0 for the M-audio Fast Track.

I tried that and audio worked better for a while and then became noisy again. I understand the Fast Track is not really supported. Is there a work-around?

---


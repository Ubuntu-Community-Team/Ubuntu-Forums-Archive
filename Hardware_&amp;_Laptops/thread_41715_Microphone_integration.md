---
title: "Microphone integration"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by Nori on 2005-06-14
Hello everyone,

After some tweaking I got the mic of my webcam working. It is now /dev/audio. My Soundcard for output is /dev/audio1. /dev/dsp* doesn't seem to work, so I set the esd-deamon to /dev/audio1.
My Problem is that I dont know how to integrate the mic-device into the desktop. Gnomemeeting recognises a Camera but doesn't get data from it. So does skype.
I'm sure /dev/audio works as my mic. I tested it with "cat /dev/audio" and got ascii-rubbish changing according to my vocal input.

Hoping for help,
Nori

---


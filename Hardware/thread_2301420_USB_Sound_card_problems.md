---
title: "USB Sound card problems"
date: 2015-11-02
forum: Hardware
---

### Post by pieter512 on 2015-11-02
Hello,
I'm trying to connect my laptop (Ubuntu 14.04) to my mixer ([JBsystems Beat 6 USB]("http://www.beglec.com/manuals/107.pdf")). It has 2 USB inputs for audio, and they both work fine when using a 1.5m cable, but when I use a longer cable (5m), my pc doesn't even detect the sound card. When I connect it to my Windows pc using the long cable, it works perfectly. Using the short cable, it's a "Micronas GmbH Composite USB-Device", according to lsusb.

Also, when I try to connect my other mixer ([Behringer UFX 1604]("http://www.music-group.com/Categories/Behringer/Mixers/Small-Format-Mixers/UFX1604/p/P0AB3")) with either one of the usb cables, there's a short delay of +/- 1 second between the moment I press play, or unmute, and the actual music coming out of the speakers. It's not latency, just the first second that gets chopped off. On Windows, this works fine, and on Ubuntu, the problem is only present when I use pulseaudio. Jack and applications that use ALSA to connect directly to the mixer work just fine. The second problem is that I have to restart my pc or kill pulseaudio and ALSA before it detects the mixer. On Windows, again, I can just unplug it and plug it back in without any problems.

Any help appreciated!
Pieter

---


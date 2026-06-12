---
title: "Microphone Problem on HP DV2"
date: 2010-09-10
forum: Hardware
---

### Post by sineau on 2010-09-10
Hi all,
How can I make built-in microphone on my HP DV2 laptop to work? I searched for it and most of the threads are about other laptops with Intel running (mine is a AMD neo).

If it helps: i run ubuntu lucid (netbook version), and  Gnome-alsa-mixer shows my sound card as IDT 92HD75B2X5.

---

### Post by sineau on 2010-09-11
Found the answer myself. First I went back to my older kernel (2.6.32-21), then i chose OSS or PulseAudio instead of ALSA in gstreamer properties. Still didn't test it with the newer kernel.

---


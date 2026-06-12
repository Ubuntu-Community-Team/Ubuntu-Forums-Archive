---
title: "Sound broken after update"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Slayer93 on 2009-04-18
I recently installed updates for my Hardy Heron version of Ubuntu. I did a system restart as required, but when it booted up again, i had absolutely no sound. The volume control on my taskbar has the muted picture, but the sound isn't muted. When I try opening volume control, it says "No volume control GStreamer plugins and/or devices found."

Any help here?

---

### Post by lemming465 on 2009-04-19
Please include the output of *lspci -v*; no one is going to be able to help you diagnose this without knowing more about the hardware involved.

---

### Post by Chris Riley on 2009-04-20
However, it does seem to be a common problem. I had the same fault when I upgraded from 7.10 to 8.04 on an AMD 64 ATI MB with onboard sound & graphics. I too asked the question, but received no replies. I then went into Synaptic Manager and deleted the most recent Linux kernel (2.6.24.24). Sound now okay, system says I still running Hardy Heron.

---


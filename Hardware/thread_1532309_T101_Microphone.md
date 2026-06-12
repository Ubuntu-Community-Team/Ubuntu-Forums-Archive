---
title: "T101 Microphone"
date: 2010-07-16
forum: Hardware
---

### Post by fishyf on 2010-07-16
The new kernel, 2.6.32-23-generic, broke the previous solution to fixing the internal microphone on the T110.

The fix is to install previous alsa module

```
sudo aptitude install linux-backports-modules-alsa-lucid-generic
```

Reboot the laptop (I can't see a simple way to restart the sound drivers)

Then run gnome-alsamixer

This should show you Mic B to Mic F. By default, Mic B is clicked. Change this to Mic F and the microphone should work.

---

### Post by fishyf on 2010-07-16
Sorry: the title was incorrect. Fixed here.

---


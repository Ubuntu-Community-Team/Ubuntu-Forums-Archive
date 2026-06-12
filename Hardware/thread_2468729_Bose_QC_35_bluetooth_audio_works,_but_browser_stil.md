---
title: "Bose QC 35 bluetooth: audio works, but browser still plays through speaker"
date: 2021-11-09
forum: Hardware
---

### Post by Minilek on 2021-11-09
Hi. I successfully paired my QC 35 wireless headphones to my laptop over bluetooth, running Ubuntu 18.04. I did this by going to System Settings -> Bluetooth, and selecting the device to connect to while it was in pairing mode. I then selected the headphones in System Settings -> Sound as the primary audio output, with "High Fidelity Playback (A2DP Sink)" as the Profile. The audio works, and now audio plays through my headphones ...except through the browser! I've tried both Chrome and Firefox, but both continue to play audio through my laptop speakers, even after restarting them (tested by watching videos on youtube.com and cnn.com). Any thoughts on why this might be happening and how to fix it?

---

### Post by ajgreeny on 2021-11-09
Switching audio from speakers to headphones on laptops is often activated by a hardware switch in headphone sockets; with Bluetooth connections that will, of course, not happen. 

You have not told us anything about your hardware but I suspect Sound Settings (pulseaudio volume control) will be the way to solve this using a software method.

---


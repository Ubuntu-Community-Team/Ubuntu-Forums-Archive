---
title: "Logitech webcam pro 9000"
date: 2011-09-13
forum: Hardware
---

### Post by madubuntuer on 2011-09-13
I have logitech wecam pro 9000. The video is working perfectly in skype. .However the sound doesn't work at all. I seem to be having difficulty recording in Gnome sound recorder. I've notcied the device doesn't appear in the gnome sound applet. However alsa can see the onboard mic. I've set the mic to capture. It says it has no playback controls.I'm running Ubuntu 10.10 with latest pulse-audio and alsa.

---

### Post by SeijiSensei on 2011-09-13
I had this problem in Kubuntu and had to tell pulseaudio to use the 9000's microphone.  I don't know how this is done in GNOME, but you have to configure pulse to handle this.  Using alsa alone probably won't work.

In general, most anything audio-related is handled by pulse.  Even if it uses alsa on the backend, the configuration is done through pulseaudio.

---

### Post by madubuntuer on 2011-09-14
Yes but I can't see the device even in padevchooser / pulse volume control

---

### Post by SeijiSensei on 2011-09-15
Maybe try purging and reinstalling alsa and pulse?

---


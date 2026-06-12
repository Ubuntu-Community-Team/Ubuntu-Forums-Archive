---
title: "Toshiba A135 S4427 No Sound"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by jlwood on 2007-05-01
Here is what worked for me. I have the ALC861VD.

Edit "/etc/modprobe.d/alsa-base", adding this line, "options snd-hda-intel position_fix=1 model=3stack"

Restart the PC


Then I went to the sound preferences, devices tab, change playback to OSS - Open Sound System.

On the voulume control, File-change device-HDA Intel (Alsa Mixer)

Then turn up all the volume controls

---


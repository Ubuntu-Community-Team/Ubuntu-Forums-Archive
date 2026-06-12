---
title: "HP dv6 sound devices not detected"
date: 2011-06-18
forum: Hardware
---

### Post by mitchell2.0 on 2011-06-18
Hi, i have an hp dv6-1203ax, and although the sound is working, it hasnt detected some devices and one isnt working properly. It has IDT HD audio

There are 4 sound devices:
Speakers and dual headphones
independent dual headphones
SPDIF dogital out via hp dock
ATI HDMI output

In windows i only use the first (which automatically switches between the speakers and headphones) and the HDMI on the graphics card.

In Ubuntu 10.10 only the speakers and dual headphones and HDMI are detected. The output works but on speakers and headphones (at the same time, not switching like is meant to). havn't tested HDMI yet, but i got the graphics card driver so it should.

Anyway, i just want to know how to get it to switch between the speakers and headphones when i plug them in. I dont need it to detect the independent headphones but it would be nice. I have the alsa drivers (came with 10.10)

EDIT: Forgot to mention that i can switch it between speakers and headphones by changing the connector in sound preferences. It just doesnt auto detect like on windows

---

### Post by lidex on 2011-06-18
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---


---
title: "No sound (only HDMI output) with ALC883, HP Pavilion Media Center 8280.            fr"
date: 2018-05-27
forum: Hardware
---

### Post by Ed_B on 2018-05-27
Hi,  I have an old machine, HP Pavilion Media Center 8280.fr.  The sound used to work fine under Ubuntu 8.04.  If I remember correctly, it worked out of box. The only thing
that can be relevant that I found was a line 
```
options snd_hda_intel model=6stack-hp 
``` in /etc/modprobe.d/alsa-base. But now under 16.04, only HDMI output on the integrated sound card (Intel, ALC883) is recognized, and there is no analogue
output.  I added the option line in /etc/modprobe.d/alsa-base, but this doesn't help.  Any idea on how to fix this?

---


---
title: "Mute speakers when plugging in head phones with ALC888 on MSI Notebook (SOLVED)"
date: 2009-05-15
forum: Hardware
---

### Post by ralph.eichelberger on 2009-05-15
I have a MSI PR211 Notebook with a Realtek ALC888 sound card.

When I plugged in my head phones, the speakers did not mute.

The solution was to add this line to /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=targa-2ch-dig

After reboot plugging in my head phones would mute / tun off the speakers.

I found that solution on these sites:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://kubuntuforums.net/forums/index.php?topic=3100371.0](http://kubuntuforums.net/forums/index.php?topic=3100371.0)

---


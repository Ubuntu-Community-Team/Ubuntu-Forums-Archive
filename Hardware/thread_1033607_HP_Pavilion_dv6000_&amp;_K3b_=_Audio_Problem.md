---
title: "HP Pavilion dv6000 &amp; K3b = Audio Problem"
date: 2009-01-07
forum: Hardware
---

### Post by gabrielitos on 2009-01-07
Hi,
I've a big problem with my laptop, a HP Pavilion dv6000: everything was working ok until I installed k3b.
I burned a dvd but, when I was going to reboot, the splash screen was strange: 4 orange bar and a bad resolution.
When I started computer again, everything seems good but the audio doesn't work anymore with alsa and pulseaudio: the audio card is correctly recognised in dmesg and the audio subsystem return from stand-by when I open a music file, but there is no sound! (I controlled the volume level, everything high and switch-on!). Neither the "tata" sound on login screen.
Only Skype works: I noticed, anyway, that in the Skype configuration, two devices are present: hw0 and a new one, hw6. When I switch to hw6 Skype works, when I use hw0 the behaviour is the same of alsa and pulseaudio.
I think I should switch everything to hw6 and/or delete hw0: how can I do it? asoundconf shows me only one device.
The audio card is a Intel HDA.

Thanks!

---


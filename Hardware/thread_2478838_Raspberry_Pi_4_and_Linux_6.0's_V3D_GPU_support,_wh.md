---
title: "Raspberry Pi 4 and Linux 6.0's V3D GPU support, when will Ubuntu benefit?"
date: 2022-09-06
forum: Hardware
---

### Post by vinnnn on 2022-09-06
Have been using Ubuntu 22.04 on the Raspberry Pi 400 as a lightweight desktop system and it makes a great, low power, silent desktop system.
The elephant in the room though is the lack of video hardware acceleration and choppy compositing which is a known issue for any aarch64 environment on Pi4 at the moment and on Ubuntu, Gnome can get laggy and video playback is all CPU bound so 4k video isn't possible and browser-based video playback really suffers.

With the recent news that the Pi 4's V3D driver has made it to Linux mainline this could really make Ubuntu desktop on the Pi 4/400 a much better experience.
I had a go of Fedora 38 Rawhide on the Pi 4 last week which is shipping with Linux 6.0-rc builds and Gnome compositing is smooth, sadly video hardware acceleration isn't there yet.

So does anyone know what the plans are for the V3D driver on Ubuntu for Raspberry Pi? Are we to wait until 23.04 or beyond or is there an effort to bring it to 22.10 for the Raspberry Pi?

---


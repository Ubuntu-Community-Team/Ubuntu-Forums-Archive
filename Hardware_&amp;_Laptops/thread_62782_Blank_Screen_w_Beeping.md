---
title: "Blank Screen w/ Beeping"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by paul-donnelly on 2005-09-05
I just experienced what is easily the most alarming crash I've ever seen. My screen went blank (while playing Neverputt) and my PC speaker started beeping at me until I turned the computer off. It was the beeps that were really surprising. I'm using the fglrx verson 6.8.0-8.8.25-0ubuntu11 video driver with an ATI Radeon 9200. Another strange thing was that /var/log/Xorg.0.log didn't show anything wrong when I checked it. My computer just froze at a blank screen when I tried to start GDM. Luckily switching "fglrx" to "ati" in xorg.conf got GDM to start again, at which point switching back to "fglrx" worked fine, so I'm up and running again. I just hope I shouldn't expect this to happen frequently.

Oh, by the way, I'm new here, so hello to all.

---


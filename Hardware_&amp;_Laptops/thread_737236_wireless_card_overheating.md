---
title: "wireless card overheating?"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by eiffel on 2008-03-27
I'm having a problem when I leave my laptop downloading from the web I often come back to it and it's completely frozen up with the caps lock and scroll lock lights flashing.

I've looked around these pages and I get the impression this is probably a hardware/heating issue.

tail message.0 gives 

Mar 27 00:55:08 eisystem kernel: [  953.356926] wlan0: tx error 0x20, buf 11!
Mar 27 00:55:08 eisystem kernel: [  953.357009] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
Mar 27 00:56:46 eisystem kernel: [ 1051.149812] wlan0: rx: 69 DUPs in 495 packets received in 10 secs

Which would seem to suggest my pcmcia wifi card is getting too hot?

I've tried to install lm-sensors but my motherboard isn't supported.

Is it my wifi card overheating, and if so what can I do about it?

---


---
title: "Trying to control fan speed, HP Pavillion dv2000"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by decoherence on 2007-07-18
Hi. I'm trying to back up and repair a friend's borked Windows laptop, an HP Pavillion dv2000. Of course I've booted from my Ubuntu live CD (7.04) to back things up safely and run clamav.

The problem is the temperature keeps ratcheting up but the fans don't come on strong enough. When it gets to around 99 degrees, the computer shuts itself off before clamscan is done. The fans never go beyond a whisper.

What I want to do is run the fans on full. Normally I'd do this by setting /proc/acpi/fan/FANx/state but there is nothing in /proc/acpi/fan/. Just wondering if anyone knows how I oughta be doing this, in this case.

Probably what I should do is take a can of air to its heat sink. But my friend has never noticed it shut down at random in Windows (with two kajillion little pieces of junk software loaded in the background, while playing fps games) so I'm more inclined to think it's a bug in acpi, hence why I want the manual control.

Anyway, I'm managing to keep the heat down by throttling the processor (Turion64 X2) but i'm watching it creep up...

any insights more than welcome!

---

### Post by Death_Sargent on 2007-07-19
man i am having the exact same kind of probelm. 

though as far as i know you can set the gnome powermanager to set it up higher. if you move it to say "preformance" everything will be set real high.

---


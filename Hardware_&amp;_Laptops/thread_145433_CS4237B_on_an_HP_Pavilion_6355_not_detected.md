---
title: "CS4237B on an HP Pavilion 6355 not detected"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by kafarnsworth on 2006-03-16
I installed Ubuntu 5.10 on my HP Pavilion 6355.  I've determined from internet sites that the sound chip is built on the mother board and as a CS4237B.  Ubuntu doesn't seem to detect the chip.  When I use the volume control I get "No volume control and/or devices found".  If tried modprobe snd-cs4232, as some sites suggest.  I've also tried adding options to /etc/modprobe.d/alsa-base, tried moving alsa-base and creating alsa (in the same directory).  I've tried adding acpi=off to my kernel parameter list.  Still no sound.

Can anyone help me, or point me to a site that might help?  I've tried as many as I could google, but none has worked yet.

Thanks,

Kaf

---


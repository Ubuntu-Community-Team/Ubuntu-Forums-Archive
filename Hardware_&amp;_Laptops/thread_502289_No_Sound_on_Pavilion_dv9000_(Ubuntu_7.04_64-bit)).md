---
title: "No Sound on Pavilion dv9000 (Ubuntu 7.04 64-bit))"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by ccmichaelson on 2007-07-16
I have no sound on my HP Pavilion dv9000 64-bit laptop running 7.04.  I have reviewed many posts, recompiled the ALSA drivers, and nothing seems to work.  I believe the problem might be my aplay-l output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm not sure why it lists my Modem - which I really don't use but I couldn't disable it in the BIOS.

---


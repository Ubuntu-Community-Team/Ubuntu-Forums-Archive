---
title: "Lenovo Extreme 1x Gen 2 - Built in HDMI not working and issues with thunderbolt dock"
date: 2020-01-04
forum: Hardware
---

### Post by cunninglogic on 2020-01-04
Ubuntu 19.10
Linux HackPad 5.3.0-24-generic #26-Ubuntu SMP Thu Nov 14 01:33:18 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Hardware:
Lenovo Extreme 1x Gen 2
[https://www.lenovo.com/us/en/laptops/thinkpad/thinkpad-x/X1-Extreme-Gen-2/p/20QVS0FP00](https://www.lenovo.com/us/en/laptops/thinkpad/thinkpad-x/X1-Extreme-Gen-2/p/20QVS0FP00)
CalDigit USB-C Pro Dock (despite name it is thunderbolt 3)
[https://www.amazon.com/gp/product/B07VL675DT/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B07VL675DT/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)

I'm trying to migrate back to linux from being on OSX for a decade, I've not used a non headless linux box in a long time (plenty of experience with embedded and servers)

Two separate but possibly somewhat related

For one, the built in HDMI port does not function, when on intel discrete graphics, or on the nvidea. The monitor seems to get a signal (does not show "no signal" error), but remains black. No second monitor in display settings, but nvidia settings shows it.

Dock issue:
Dock is detected as thunderbolt, display ports behave identical to the internal hdmi port. Usb storage works, external keyboard works, blue tooth mouse does not (but does with built in usb ports).


I need a secondary display, so any assistance will be welcome. I'm open to buying a different dock if that will get this working. I absolutely hate the latest Apple hardware, really want to get off of those...

---

### Post by cunninglogic on 2020-01-05
For the dock I got it working solid by
Disabling kernel DMA protection in bios
Disabling thunderbold 3 security
Switching to just nvidia graphics

This allows me to use the displayport, which works for my needs at home.


I still need the internal hdmi port working but ive had no luck

---

### Post by cunninglogic on 2020-01-06
Internal HDMI was fixed by:
Switching to just nvidia graphics
Manually setting the refresh rate to the monitor spec.

---


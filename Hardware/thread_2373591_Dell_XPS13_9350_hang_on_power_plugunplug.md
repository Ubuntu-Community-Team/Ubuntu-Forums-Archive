---
title: "Dell XPS13 9350 hang on power plug/unplug"
date: 2017-10-07
forum: Hardware
---

### Post by diskdur on 2017-10-07
Hi


I'd like to report a problem with my Dell XPS13 9350, and if possible gather some ideas to try to understand what happens.


Currently running Ubuntu 17.04 (up to date) on my xps13 (bios 1.5.1 up to date), each time I plug (or unplug) the power cable, my ubuntu is hanging the whole laptop (no working key, screen frozen, laptop does not ping anymore from another system).


The facts :
* a dell bios upgrade is responsible of this issue (1.4.14 was the last bios version OK, as far as I remember)
* everything works fine under windows 10
* once hung, only a long keypress on the power button manage to poweroff the laptop
* I'm now obliged to use hibernate in ubuntu, before plugging/unplugging the power cable.
* after reboot, nothing in the logs /var/log/{syslog,kern.log}, except a classical boot log.


I would be very pleased to test some ideas to produce some logs, and finally understand the issue.


Thanks & Regards.


dd

---


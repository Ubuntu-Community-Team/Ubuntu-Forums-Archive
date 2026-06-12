---
title: "Problems with HP840C paraller printer"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by TADsince1995 on 2006-12-10
Hi guys!

I've a weird problem with my parallel printer HP840C. I've parport, parport_pc and lp modules running. But when I try to add my printer with System -> Administration > printers or directly with cups on localhost:631 I cannot manage to have it properly working.

I add it with parport:/dev/lp0, using my previous slackware installation, the printer worked perfectly with the same configuration. But now when I launch a print, the printer starts to print dozens of white pages with only one row of strange characters and never stops!!! (I have to stop it brutally turning it off, and then it restarts when I turn it on)

I tried to use printconf, which detects a HP842 printer on parport:/dev/lp0 with hpijs driver, but the problem persists!!!

Please help!

Thank you in advance!

TAD

---


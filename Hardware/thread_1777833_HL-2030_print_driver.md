---
title: "HL-2030 print driver"
date: 2011-06-08
forum: Hardware
---

### Post by Jakobdkp on 2011-06-08
Hi.

I just upgraded to 11.04, and it seems the driver for my Brother HL-2030 printer is broken.

When I print text, the letters are ugly and in very low resolution.

I have tried switching to all available drivers for the HL-2030, as well as the HL-2140. I found an HL-2040 PPD file online, and had no problem installing it, but it still looks like crap.

Is it a driver problem? Have I failed to check a box somewhere?

The HL-2040 driver worked in 10.04, but is unavailable in 11.04.


Does anyone have a clue as toa solution?


/J

---

### Post by Siknitrus on 2011-09-10
Hi. 

I had the same problem. I solved it with the following steps:

[LIST=1]
[*]run system-config-printer
[*]Add printer
[*]Choose "Other"
[*]Enter URI: usb://Brother/HL-2030%20series
[*]Choose "Provide PPD file" and select file: /usr/share/ppd/Brother/HL2030.ppd
[*]Finish other question and it's done
[/LIST]
For PPD file you need to install brother-cups-wrapper-laser package from Multiverse repo.

I hope it will help someone.

---


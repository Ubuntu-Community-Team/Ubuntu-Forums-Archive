---
title: "Radeon 9600 with oss ati driver - hard lockups"
date: 2008-07-28
forum: Hardware
---

### Post by aaronp on 2008-07-28
All,

Had some problems with my new AGP Radeon 9600 using the fglrx driver. Got rid of that driver and using the open source ati driver and a couple of problems. I'm running Hardy 8.04

1. Screen resolutions. I have previously been able to get quite high resolutions on my 19in Compaq P920 monitor. Since changing to the current driver the highest I can get is 1280 x 1024 (85hz). 1600 x 1200 is available to select but it does not function correctly (fuzzy misrendered section on the right and bottom of the screen)

2. Hard lockups. After changing the driver I was running compiz-fusion affects all day without issue. Suddenly I got a hard lock (mouse moves but nothing else possible - power button to restart PC). Then almost immediately got another hard lock (this time no mouse movement either).

Assuming it was compiz I disabled it and another hard lock came within about 20 minutes (no mouse again). After rebooting again I got another one (this time WITH mouse movement again but nothing else). I'm perplexed by this because I had assumed it was to do with the desktop affects.

Attached my xorg.conf - hopefully this helps.

Any guidance is appreciated.

Thanks
Aaron

---


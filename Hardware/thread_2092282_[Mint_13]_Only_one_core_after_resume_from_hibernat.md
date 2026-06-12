---
title: "[Mint 13] Only one core after resume from hibernation."
date: 2012-12-07
forum: Hardware
---

### Post by darzur on 2012-12-07
Hi folks,

It's my first post here, as I'm (almost) happy linux user since a week. My problem is that after resuming from hibernation my system sees only one CPU core. Then this core can be loaded only to 50% and second (not present in system) core is most probably working at full load as CPU temperature very quickly goes high. I've tried pm-utils and uswsusp with same effect. TOI doesn't work at all - it shows kernel panic during resume.

My system as an old Dell GX270 with PIV HT 2.8, 3gigs of RAM and i865 integrated graphics. Disabling HT in BIOS solves problem, but then I have only one core available all the time so it's not a way I want to go. Distro I use is Mint 13 (12.04) MATE x86 with kernel updated to 3.4. I've updated kernel with hope to solve this hibernation problem, but it didn't helped at all. So I hope someone here will be able to help. :)

---


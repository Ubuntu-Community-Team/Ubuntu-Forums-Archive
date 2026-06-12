---
title: "Unusual sound issue."
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by Roybotnik on 2005-09-01
Hi everyone,

I just did a clean install of hoary on my laptop.  It has an integrated ALi5451 chipset which is supported by alsa.  I followed the guide in the stickied thread at the top of this forum, successfully compiled my kernel modules with --with-cards=ali5451 and whatnot, but for some reason after rebooting I have no sound.  When I try to run alsamixer I get the following:

alsamixer: function snd_ctl_open failed for default: No such file or directory

I also have the following added into my /etc/modules:
snd-pcm-oss
snd-ali5451
snd-mixer-oss

I have no sound whatsoever, and my comp beeps 7 or 8 times while booting up with amixer crap flying down the screen.  I'm not exactly a linux pro so any help would be greatly appreciated =).

---

### Post by Roybotnik on 2005-09-01
bump?

---


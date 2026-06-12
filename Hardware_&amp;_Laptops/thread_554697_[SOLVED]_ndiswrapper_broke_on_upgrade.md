---
title: "[SOLVED] ndiswrapper broke on upgrade"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by Achetar on 2007-09-19
Alright, just now upgraded to Feisty, after doing it several months ago, and it breaking everything but ndiswrapper. So i did a fresh install of 6.10 and just now did another upgrade. Well, this time it only broke ndiswrapper.
:confused:
Now when i use 'sudo modprobe ndiswrapper' it gives me the following error:

```
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

```

Help me plz! I have been using Ubuntu for almost a year now and I don't want to have to give it up because of my stupid Linksys WPC54G v3 Card (of course i wouldn't, I'd go out and buy a supported card, but i dont really want to do that either)

Oh, and my sig is for in Edg

[SOLVED] You have to make the latest stable ndiswrapper (1.47) from the source. This fixed it

---


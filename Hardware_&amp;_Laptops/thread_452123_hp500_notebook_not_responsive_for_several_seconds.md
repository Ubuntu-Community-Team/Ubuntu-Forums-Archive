---
title: "hp500 notebook not responsive for several seconds"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by hehe on 2007-05-23
Hi,

I'm a new ubuntu user. I've installed ubuntu 7.04 for a couple of weeks on hp500 notebook (pentium m 2.13GHz, 512MB). I have a problem with the laptop randomly going not responsive for several seconds. I can still click on something, switch between terminals, but I can't do 'ls, cat, vi (anything related to file I think)' and if xmms is running then it'll get paused too. After several seconds (10-30s) it get back to normal.

From my search in this forum I suspect it is related to acpi, powernowd or something like that. Based on that I tried to add several kernel parameters on boot (acpi=off noacpi nolacpi idle=poll), and after I get the computer booted I do '/etc/init.d/powernowd stop' as root, but it didn't help.

Anyone have the same problem or solution for me?

Thanks

---


---
title: "3D working but no results in glxgears"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by tdp on 2005-10-10
Hello all,

Very new to the linux world, and even newer to the world of ubuntu (just migrated from Suse 9.3). 

My ubuntu installtion has gone pretty well so far (will be completing further testing). However, when I run glxgears, I don't get any fps information. The gears all rotate very smoothly. Is there some config file I need to edit to get working.

Any help would bve great .

TDP.

---

### Post by tdp on 2005-10-11
Man!!! I'm such a newbie. I'm not even using Hoary, I'm using Breezy.

Anyway, fps out via stdout has been disabled by default in Breezy. Use the following switch to fps info (the reason will become clear):-

glxgears -iacknowledgethatthistoolisnotabenchmark

I hope that this helps any Breezy users that have come across this.


Regards

TDP.

***Edit***

I now agree that Glxgears is not the best way to test your gfx performance. Under Suse 9.3 I'm getting higher fps, but screensavers and games run slower that in Breezy (which is giving me very low fps).

I wonder if that is a Linux version of 3DMark?

---


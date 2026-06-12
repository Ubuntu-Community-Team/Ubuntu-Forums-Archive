---
title: "Radeon Driver on Eee PC 1215t"
date: 2011-04-27
forum: Hardware
---

### Post by Arithrix on 2011-04-27
Hi,

I have an Eee PC 1215t netbook with an ATI Radeon HD 4250 card.

Using Ubuntu 11.04

My problem is when I install the proprietary ATI driver, it works fine with games and video, but when I open up a flash based website the computer comes to a crawl.

If I use the OSS drivers flash and videos work great, but old Open GL games like Neverwinter Nights which I enjoy playing are unplayable.  Also the power management sucks with the OSS drivers, I get about 2.5 extra hours of battery life with the proprietary drivers.

Any tips on improving flash performance with the proprietary ATI driver?  Ive searched, but none of the previous suggestions have worked for me.

---

### Post by Yellow Pasque on 2011-04-27
For some reason, Ubuntu 11.04 doesn't turn on the OSS power management goodness by default. I don't even know if they compile it into the kernel. I haven;t been successful with dynpm: [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

Supposedly, with latest power management, the open-source driver is a lot closer to Catalyst with battery life.

---

### Post by Arithrix on 2011-04-28
Thx.  I'll check out that power feature if I cant get catalyst to speed up.  It's very strange, everything works great and quick until I open up a browser and go to a flash page, then everything comes to a crawl.

Any other ideas?

---


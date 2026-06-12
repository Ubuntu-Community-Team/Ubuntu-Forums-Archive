---
title: "Any news on..."
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by mike66939 on 2009-08-14
Has there been any news lately on radeon x1200 graphic driver on ubuntu jaunty :confused:? really don't want to downgrade.

---

### Post by Nburnes on 2009-08-14
Idk if this is of much or any help, but I am running Karmic Alpha 3 superbly with Radeon x1250 graphics.

---

### Post by Mark Phelps on 2009-08-16
> **mike66939 said:**
> Has there been any news lately on radeon x1200 graphic driver on ubuntu jaunty :confused:? really don't want to downgrade.

If you're asking about the restricted driver from AMD/ATI -- there is not going to BE any news.  ATI made it clear in their Release Notes when they dropped support with Catalyst 9.4, that they would NOT be providing any future driver updates for what they now consider "legacy" cards.  Yeah, I know there have been rumours going around that ATI would continue support but on a Quarterly basis -- but that's NOT what their Release Notes said.

The other problem is an incompatibility between the Catalyst drivers and the version of the XServer which prevented the "legacy" Catalyst drivers from continuing to work in Jaunty.  I've heard nothing to indicate that this is being "fixed" in Jaunty.

As to Karmic, unless AMD/ATI has changed their minds, there are not going to be restricted drivers there, either.

Remember, Ubuntu installs the open source drivers by default, and unless you're doing hard core 3D gaming, those drivers should work just fine for you.

---

### Post by psycho5 on 2009-10-14
So, in other words... I have an onboard ati x1200 series card, the drivers from ati.com won't work on Ubuntu 9.04, even though the card is listed there? By work I mean, propriety drivers. If that's the case, then that really sucks. 

So which cards onwards are being support with cat 9.4? I mean which is the 'earliest' card that will work?

---


---
title: "New Install -- System Hangs"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by grandpavic on 2008-12-31
I have, after great effort, installed ver 8.10. When the system boots, it gets to the splash screen asking for the user name (screen is in wrong resolution which I can manually change) and then after about 20 seconds or so the system hangs with key board numeric lock and caps lock indicator lights flashing. The only way out of this is to power down the system and restart it.

I am installing this on an older Dell Latitude C800.

When I run the full graphics based live cd, I get the same result.

So where do I go from here?

TIA

---

### Post by oilchangeguy on 2008-12-31
> **grandpavic said:**
> I have, after great effort, installed ver 8.10. When the system boots, it gets to the splash screen asking for the user name (screen is in wrong resolution which I can manually change) and then after about 20 seconds or so the system hangs with key board numeric lock and caps lock indicator lights flashing. The only way out of this is to power down the system and restart it.

I am installing this on an older Dell Latitude C800.

When I run the full graphics based live cd, I get the same result.

So where do I go from here?

TIA

define older dell. system specs please. cpu speed, amount of ram, and hard drive size.

---

### Post by grandpavic on 2008-12-31
> **oilchangeguy said:**
> define older dell. system specs please. cpu speed, amount of ram, and hard drive size.

Well, its not that old!!

I have been running various versions of openSUSE on it for about 5 years now. And I decided after some frustration to switch!

It has an 850 mghz processor, 20 gb of hard drive available to Linux and 512 mb of memory (some used for the graphics display).

It is a dual boot machine with Windows 2k. There is a common sharred vfat formatted data area.

I don't think that there is a resource prolem.

---

### Post by grandpavic on 2008-12-31
Well here is more info.

If I remove the pc-card wireless network adapter, the system actually boots. I can enter my username a password. Then I get the following error:

There is a problem with the configuration server (/usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status256)

Before I get this message, I hear the login music, but desktop never appears!

<ctrl><shft><Backspace> will restart the graphics back to the login point

More info

If I remove the wireless card, the live cd actually works. As soon as I plugin the wireless card, the system hangs with the flashing keyboard lights.

---


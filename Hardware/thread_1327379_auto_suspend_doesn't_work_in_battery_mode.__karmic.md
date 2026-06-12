---
title: "auto suspend doesn't work in battery mode.  karmic"
date: 2009-11-15
forum: Hardware
---

### Post by applejuicekiss on 2009-11-15
when running on battery netbook won't automatically suspend to ram as set in Power Management Prefs.

manual suspend-to-ram works fine if i select it from the menu or function key, either in battery or AC power mode.  automatic suspend-to-ram works fine when running on AC power.  however, when running in battery mode, the machine won't automatically suspend-to-ram after the specified period of inactivity or when battery becomes critically low.  i see this with no external devices attached (no sd cards, usb, etc) and with no apps running aside from those that load by default on login.

acer aspire one D250
atom n270 1.6 GHz (32bit)
1 gig ram
Ubuntu Karmic Koala (32bit)(fully updated from 9.10 beta release clean install)
- can't remember which daily build i started with.  it was several weeks before the official release.  fully updated since then.  

finally, i know this is minor, especially after reading through all the other threads about borked power management, freezing after resume etc. i'd like to get this fixed nontheless.  thanks in advance for suggestions.

---

### Post by jj9 on 2009-12-23
confirm, same problem.  from the logs, it looks like it suspends then immediately resumes.  acer 1410 running karmic.

---


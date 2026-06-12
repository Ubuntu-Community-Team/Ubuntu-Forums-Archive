---
title: "Slow Firefox: solved by using a different browser"
date: 2008-12-01
forum: General Help
---

### Post by Roostey on 2008-12-01
This is just a note for anyone else who might be experiencing degraded system performance that's related to Firefox, since I've noticed a few threads on the issue.

What's happening on my system is that the majority of web pages that have images and are longer than about two screens cause Firefox to randomly slow to a crawl.  As an example, scrolling down pages at Slashdot uses 100% of one of my CPU cores and results in a screen refresh every two or three seconds, sometimes stalling the whole PC for more than five seconds at a time.  Changing tabs takes up to five seconds.  Drop down menus take several seconds to appear.

Additionally, the problem spills over into Gnome itself, with the main menu also affected while Firefox is displaying one of the offending pages and changing applications takes up to five seconds as well.

After battling with this problem for a while (including installing the latest beta nVidia drivers and Flash), I've had enough.  I've got a decent PC and Firefox is just killing it.  The cause would appear to be a problem with the new Cairo renderer, specifically relating to images as turning off image loading fixes it.  There's nothing that Canonical can really do about it and Mozilla are well aware of the problem.  Judging by Mozilla's support forums a fix is likely a long way off.

Anyway, I've just installed Opera and it's completely solved the problem.  Gnome and browsing is snappy again, web page scrolling keeps up with the mouse and tabs switch instantly.  So, there's the solution for anyone else who's suffering through this nightmare: Use a different browser.

---


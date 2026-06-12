---
title: "Closing lid doesn't shut off display"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by Zeddicus on 2006-11-06
Hiya.

Using a Dapper system, my machines former behavior was that when I closed my laptop lid, the screen would turn off and kscreensaver would start.  All fine and good.

Well, *something* happened recently and has removed this functionality!

The lid button no longer generates events in /proc/acpi/event (and hence, scripts in /etc/acpi are never called)... and I haven't the slightest clue why not. :/

Any help?

---


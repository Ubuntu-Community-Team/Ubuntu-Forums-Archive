---
title: "ThinkPad T61: resume from sleep takes a long time on Gutsy: how to troubleshoot?"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by softtower on 2008-04-05
I have ThinkPad T61 with Intel X3100 video card. My /etc/default/acpi-support file is updated according to ThinkWiki: it has "DOUBLE_CONSOLE_SWITCH=true". The Laptop susbends/hibernates, but *sometimes* it takes **forever** to resume (wake up): several minutes as opposed to seconds.

Where do I begin to troubleshoot? What log files should I look in?

---

### Post by sdennie on 2008-04-05
A reasonable start would be to just look at the acpid log after a long resume (/var/log/acpid).  It has timestamps so, you should be able to see what part of the resume is taking so long.  After that, you can probably narrow things down to see exactly what the problem is.

---


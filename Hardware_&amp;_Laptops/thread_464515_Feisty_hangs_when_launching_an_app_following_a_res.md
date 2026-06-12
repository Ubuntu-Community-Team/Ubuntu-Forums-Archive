---
title: "Feisty hangs when launching an app following a resume"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by mylesorme on 2007-06-04
I'm running Feisty Fawn with updates on a Thinkpad T41. The latest Kernel updates resolved the blank screen on resume. Now when I resume from suspend to ram applications that were open work fine, but if I try to launch an application the application fails to launch and the laptop hangs with lots of disk activity. I have no idea how to find out more what is happening. any  ideas anyone? On further investigation... the disk thrashing starts after about a minute, until then then everything apparently functions. What can I do to diagnose further?

---

### Post by Didjit on 2007-06-06
I had a similar problem with the older kernel. On resume my drive would be remounted as read only. Some bug with my Sata drive. Try digging though your syslog and see if any strange disk i/o stuff shows.

Didjit

---

### Post by mylesorme on 2007-06-06
well there are loads of evms-engine log entries that do seem to indicate errors, though I have no idea what they all mean or what to do about them... another research project

---


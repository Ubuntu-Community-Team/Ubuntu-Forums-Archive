---
title: "HP Wireless Deskjet won't stay online"
date: 2011-01-27
forum: Hardware
---

### Post by dayv2005 on 2011-01-27
I recently set up a HP Wireless Deskjet F4580 (F4500 series). It works fine at first from my computer via wireless. After about 30-45 mins it won't work. Any print job i send to that printer won't print. It is almost like the printer went to sleep and won't wake back up to print the job. I set up a static IP for it and looked all over the configuration page for any timeout sleep mode or anything. I couldn't find a single thing. I can not figure this out to save my life. Has anyone else experienced this and if so what did you do to fix it?

The only thing in the settings that I wasn't sure was ad-hoc settings i did nothing to those. Thanks.

---

### Post by dayv2005 on 2011-01-27
> **dayv2005 said:**
> I recently set up a HP Wireless Deskjet F4580 (F4500 series). It works fine at first from my computer via wireless. After about 30-45 mins it won't work. Any print job i send to that printer won't print. It is almost like the printer went to sleep and won't wake back up to print the job. I set up a static IP for it and looked all over the configuration page for any timeout sleep mode or anything. I couldn't find a single thing. I can not figure this out to save my life. Has anyone else experienced this and if so what did you do to fix it?

The only thing in the settings that I wasn't sure was ad-hoc settings i did nothing to those. Thanks.

The issue has been resolved. I believe the problem was upnp was enabled on my router. I disabled it and i believe the advertisement period was causing this issue. I just manually configured all my port forwarding and it seemed to have done the trick.

---


---
title: "Dell D820 wont resume"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by slick_rick on 2006-12-07
My D820 won't resume from a hibernate.  I hit "hibernate" in the shutdown menu and it seems to do so.  However when I boot it back up it boots up like normal, it does not resume the suspended session.

From what I understand the hibernate sequence should write the contents of RAM to the swap file, then the kernel should detect the memory image on boot and use it instead of booting.  Is there any way to debug this process and find out why it isn't working?  I looked through the dmesg log but didn't see anything...

THanks!

---


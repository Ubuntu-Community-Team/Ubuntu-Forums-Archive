---
title: "HP BIOS update / upgrade via USB boot"
date: 2011-04-18
forum: Hardware
---

### Post by krazyd on 2011-04-18
For anyone who is trying to flash the BIOS of their HP machine by creating a bootable USB stick, you *must* use a USB stick which is smaller than 4GB! Otherwise, you will get an error like "Invalid System Disk".

I just spent ages trying to figure this out :-/. Eventually I got it to work on an old 1GB stick, but I assume 2GB would work too.

I just wanted to put this information up somewhere because HP make no mention of it in their documentation, their software happily creates broken 4GB+ "bootable" USB drives, and I couldn't find it anywhere else on the net.

---

### Post by metromari on 2011-05-28
Thanks a bunch, I would never have figured that out. I pulled out an ancient 256MB stick and it worked.

Now if I could figure out how to get it to boot from CD...now it is just freezing...

---


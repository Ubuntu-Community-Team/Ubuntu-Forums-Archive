---
title: "PAE not allowing 4GB RAM on 10.04"
date: 2010-12-28
forum: Hardware
---

### Post by tsunamikitsune on 2010-12-28
I just installed some new RAM into my Ubuntu server (512MB to a slick 4GB), but I noticed it only used about 3GB. After doing a bit of searching online, I learned that my 32-bit installation was to blame and that installing a PAE kernel would fix it.

Well, I [followed the directions]("https://help.ubuntu.com/community/EnablingPAE"), but I'm still getting a 3GB readout from "free -m". The system lets me know I have 4096MB on boot up, but not when I check within Ubuntu.

Any idea what the issue could be?

---


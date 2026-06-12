---
title: "Which storage configuration to use?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by wesg on 2009-04-26
I've been wracking my brain trying to decide which drive configuration I"m going to use for my new Jaunty file server. Hopefully some of the users here can help me decide.

I currently have a 750GB drive I would like to use in the server, and will be purchasing an 80 GB drive to hold the OS independently, along with maybe a 1.5TB drive for main storage. I'm looking for a system that can expand in the future, but still maintain some level of redundancy while not spending a fortune (tall order).

Choices:
- RAID1 -> low storage vs investment, cannot add drives in the future
- independent drives w/ scripted backup -> easily added to, confusing file structure
- LVM -> very convenient to add to the pool, but lacks redundancy.

Any suggestions as to how I can overcome some of these shortcomings? How much data is required to maintain parity with an LVM system? If I have a 1.5TB drive, for example, will a 750GB drive drive be able to maintain parity?

---


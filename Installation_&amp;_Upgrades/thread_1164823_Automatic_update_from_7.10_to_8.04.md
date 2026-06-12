---
title: "Automatic update from 7.10 to 8.04?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by MoriyaMinakata on 2009-05-20
So, it looks like they are forcing me to update to 8.04.
Is the updater fully automated? Like, no user interaction needed?

My PC that is running 7.10 is being used as a server and has no kb, mouse or monitor.

All updates are done remotely.

---

### Post by MoriyaMinakata on 2009-05-26
Anyone?
Please help me.

---

### Post by Girl™ on 2009-05-26
What you can do is edit */etc/apt/sources.list* to say *hardy* instead of *gutsy*. After that you can do an *aptitude update && aptitude safe-upgrade && aptitude dist-upgrade*.

There will be some user interaction needed, but that pretty much consists of hitting the enter key.

---


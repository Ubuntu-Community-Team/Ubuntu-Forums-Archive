---
title: "Can't see existing Windows RAID"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by enroscado on 2009-11-11
Hello everybody.

I have an Asus P6T Deluxe V2, with 2 x 500GB HDDs in RAID 0 and Windows 7.

On separate 74GB HDD I insatalled Ubuntu 9.04.

Everything works like a charm, but i can't get Ubuntu to see the RAID, and I don't want to mess it up, because i would hate to loose any data.

Any help would be appreciated, since I've been stuck in this for a couple of days now.

Cheers

---

### Post by enroscado on 2009-11-12
Bump

---

### Post by enroscado on 2009-12-21
Well, thanks for all the help. Going back to windows...

---

### Post by darkod on 2009-12-21
Ubuntu 9.04 can't see fakeraid by default, if that's what you have.
First, you didn't specified what kind of raid setup you have. If using onboard mobo raid, that's fakeraid.

In ubuntu you can try installing dmraid package. That should see the fakeraid setup.

---


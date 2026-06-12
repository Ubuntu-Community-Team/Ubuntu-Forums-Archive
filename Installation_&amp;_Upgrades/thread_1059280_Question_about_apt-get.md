---
title: "Question about apt-get"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by GrouchoMarx on 2009-02-03
I have a question about [selective upgrading from intrepid-proposed]("https://wiki.ubuntu.com/Testing/EnableProposed").

I just want to make sure that I understand this priority stuff. Isn't the first entry in /etc/apt/preferences unecessary:
```
Package: *
Pin: release a=intrepid-updates
Pin-Priority: 900

Package: *
Pin: release a=intrepid-proposed
Pin-Priority: 400
```
Won't intrepid-updates default to 500 anyways?

---

### Post by GrouchoMarx on 2009-02-07
Well, in case anyone is interested, it is indeed unnecessary to include the intrepid-updates entry as the default priority is 500.

---


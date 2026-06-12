---
title: "Ubuntus hardware indetification is killing me"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by blaster32 on 2007-11-17
Hi,

I'm having an problem with Ubuntus hardware detection.
I have 5 hard disks installed and each of those is working fine, but their location in /dev changes daily. Today, my home drive could be /dev/sda1 and my backup drive could be /dev/sdb1, tomorrow it could be the other way around or completely different. Its pretty impossible to write shell script depending on mount points that way.

I'd be glad for some advice here :)

---

### Post by blaster32 on 2007-11-17
Solved it with UUID, at least I hope so ;)

---


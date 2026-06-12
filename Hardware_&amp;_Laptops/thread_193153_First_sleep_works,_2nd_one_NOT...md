---
title: "First sleep works, 2nd one NOT.."
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by Nevermore on 2006-06-09
I am experiencing the following problem with my Laptop a panasonic CF73.
the first time it goes on sleep it works flawlessly.
if i try to sleep it again in the same session it DOESN't go sleep anymore..
any idea what can be that? and how can i track it and hunt it down?
thanks

SOLVED: i blacklisted pcmcia_core and pcmcia modules which caused error (couldn't take off power to pcmcia socket) and stopped sleep.

---


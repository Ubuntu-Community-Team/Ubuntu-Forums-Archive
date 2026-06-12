---
title: "Got my suspend working! (HP ZT3000)"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by natesully on 2007-02-17
Wow, I just finally got suspend to work.  The problem was usplash, and using the radeonfb console driver.  Simply by getting rid of both, my system can now standby like windows can!  This took a while to get working, hopefully this info will help someone else.

It's an HP ZT3000 laptop, with a radeon 9200.

---

### Post by natesully on 2007-02-17
Oops, forgot to mention- you need to add acpi_sleep=s3_bios to your kernel boot parameters.

---


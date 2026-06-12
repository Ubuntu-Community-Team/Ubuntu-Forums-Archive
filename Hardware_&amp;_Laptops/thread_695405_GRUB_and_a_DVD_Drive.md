---
title: "GRUB and a DVD Drive"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by gsmonk on 2008-02-13
I installed 7.10 Server using a DVD drive from another system, I have 4 HDDs in the server and no CD/DVD drives so I had to just swap it out for a bit... Here's my problem, when I take the DVD drive out, I'm getting a GRUB load error. Anyone know how to fix this? I've never really used GRUB and have no idea on how it's configured.

---

### Post by mrsteveman1 on 2008-02-13
What are the hard drives set for with the jumpers?

Are they all set to cable select? Sometimes swapping out a dvd drive for a hard drive can cause problems depending on the HD settings (which ones are master/slave etc)

You might also check which drive your bios is set to boot first, and also check which partition ubuntu is set to root itself from.

---


---
title: "Radeon Mobility 9000"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by radicaldreamer on 2007-05-01
I have a dell inspiron 8200 with a 2.0ghz p4, 1gb ram and a radeon 9000. My problem is that desktop effects are painfully slow. Im guessing this is because there is no hardware acceleration enabled.

Does anyone know this is in fact the reason and how to fix it?

---

### Post by madmetal on 2007-05-01
> **radicaldreamer said:**
> I have a dell inspiron 8200 with a 2.0ghz p4, 1gb ram and a radeon 9000. My problem is that desktop effects are painfully slow. Im guessing this is because there is no hardware acceleration enabled.

Does anyone know this is in fact the reason and how to fix it?

open a terminal and write
glxinfo | grep direct
jf the answer is 
direct rendering: Yes 
then your 3D acceleration is ok..
othewise you have to install ATi drivers..
look at system >> administration >> restricted drivers manager for ATi drivers..

UAResolved.

---


---
title: "Can I swap a mobo/CPU/GPU on an existing install?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by scottlindner on 2008-12-30
My Ubuntu 8.0.4 motherboard died.  Will Ubuntu be tolerant to swapping this hardware without reinstalling?

Cheers,
Scott

---

### Post by cariboo on 2008-12-30
THe short answer is yes, Ubuntu uses a generic kernel, which means it should work with almost anything. The only thing you may have problems with, is if the motherboard uses bleeding edge hardware, there may not be drivers for some of it.

Jim

---

### Post by scottlindner on 2008-12-30
> **cariboo907 said:**
> THe short answer is yes, Ubuntu uses a generic kernel, which means it should work with almost anything. The only thing you may have problems with, is if the motherboard uses bleeding edge hardware, there may not be drivers for some of it.

Jim

The old motherboard that died was purchased in 2002, the replacement was purchased in 2004.  Both are Asus motherboards.  Think I'm going to be OK?  :P

Thanks for the post.  This is great news.  Assuming my problem didn't corrupt my hard disks, I'll be up and running again very quickly.

Cheers,
Scott

---

### Post by stderr on 2008-12-30
My Asus mobo moreorless died (again) recently under 8.04, and I moved about as far away from the JMicron and nVIDIA SATA controllers as I could.

The move was Asus (AMD skt939, nForce etc) to Gigabyte (Intel LGA755, Intel... ) and as you can see involved a CPU move (AMD to Intel) too. 

I was expecting a little trouble, but I never noticed any issues arising on my 8.04 installation as a result of the switch.

Good luck, but I'm sure it'll be fine.

---

### Post by scottlindner on 2009-01-04
Thanks everyone.  I did my motherboard upgrade this morning.  For the most part I had no problems as everyone suggested.  The only problem I did have is with the motherboard network controllers.  The new motherboard has two NICs and I can't get either to work properly.  I installed an old PCI NIC and it's working fine.

Cheers,
Scott

---


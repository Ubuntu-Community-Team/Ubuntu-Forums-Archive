---
title: "Lackluster performance on Core i7 Dell M6500"
date: 2010-10-15
forum: Hardware
---

### Post by chanders on 2010-10-15
I just got my Dell M6500 and the first thing I did was remove Win7 thinking that it would fly with 10.10. Man was I wrong. Just to install Office7 using wine pushes all 8 cores! Comparing this to my Sempron 140 desktop, the desktop blows this away in performance. The specs of this machine is incredible and quite frankly I am very disappointed. I think I will have to wait it out until 11.04 comes out.

I am running the AMD64 version of 10.10

---

### Post by Dark_Stang on 2010-10-15
No way! You mean windows software runs better on Windows!? *GASP*

---

### Post by chanders on 2010-10-15
If you read my post properly I said "Install" not "run".  This incident is not limited to wine but overall usage. I just provided the screenshot as that is what I was doing at the time. Thanks for your reply though, it surely was helpful :roll:

Does anyone know if there are any tweaks that can be applied to get better performance out of the Core i7 on Ubuntu AMD64?

---

### Post by Dark_Stang on 2010-10-15
That's easy, use native software. Wine is nice, but it isn't going to do everything Windows will do. If you need that, either run a virtual machine for light work or dual boot if you're going to do a lot of hardware intense things. 

Make sure your graphics card drivers are installed and workin correctly. If they aren't, you're pushing all the work onto your processor which makes for a very slow computer.

---

### Post by chanders on 2010-10-15
Thanks. I really shouldn't have put up the wine thing. The truth is I think that 10.10 doesn't really perform as I was expecting on this laptop given it has 8GB of ram and a 920 Core i7 processor using any native linux apps. I am running the proprietary Nvidia driver and all packages from the repositories are updated.

---

### Post by bedge on 2011-03-16
Run windows under virtualbox. Allocate 2 CPUs and office 2010 flies.
Windows itself is faster under vbox than native. Go figure.

---

### Post by BHEJU on 2011-03-16
I don't think it's related to Ubuntu. I have one C2D with 3gig ram and second with Core-I5 and 6gig of ram. I don't see any perf diff between them. I don't think any Core-I* are better at per than C2D. Yes, the Core-I' will give you better power and heat numbers and that's good for laptops.. But if you want perf. You might want to look at core2Quads. I have my work desktop with c2q and 8gig of ram and that is a beast of a machine.

Cheers,

---


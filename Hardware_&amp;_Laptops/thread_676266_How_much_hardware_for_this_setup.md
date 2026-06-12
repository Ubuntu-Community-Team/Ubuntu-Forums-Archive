---
title: "How much hardware for this setup?"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by mcouture on 2008-01-23
I'm planning on building a machine based on Ubuntu and running a couple VMWare systems on it.   This is a home project.  This will be my primary PC.

I want to be able to have:

- my primary desktop running the usual email, Internet browsing, video editing etc
- an Ubuntu server running LAMP, ZoneMinder for my home security system, and be the core storage server for the other PCs in the house (samba shared)
- a Windows desktop partition for those one-off applications


I was thinking of:

ABIT IP35 Pro
Intel 6600 Quad Processor
4GB RAM
(what video card? 8600GT?)
320GB HD for booting

I'll be attaching my 4 existing drives to make up my storage (remaking it into LVM maybe)

Question #1:  Will this be enough or too much hardware?

Question #2: Should I just do 1 big LVM or go with what I'm thinking?  What is easier to manage?

---

### Post by nethbar on 2008-01-24
Hard drives are always a drag on system performance; I'd set up a RAID 0 array for your most accessed data (VM images maybe?)

Just make sure that your run the drives off of separate controllers.  (No PATA Master and Slave).

Beyond that, it sounds like a great system.  In fact, I'd make **sure** you stripe your drives otherwise they'll be the slowest part on the system by far.

---


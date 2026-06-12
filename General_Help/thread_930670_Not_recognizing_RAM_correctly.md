---
title: "Not recognizing RAM correctly"
date: 2008-09-26
forum: General Help
---

### Post by questionaire on 2008-09-26
I have 4 GB of RAM on my hp 8510p but Ubuntu only recognizes/utilizes 3GB.  Does anyone know why Ubuntu would not properly recognize the pre-installed RAM?  

I am fairly new to linux, so please keep the answers pretty basic if possible. 

Also, I am running 8.04

---

### Post by Linux&amp;Gsus on 2008-09-26
I'm assuming you have a 32bit version of the OS installed whcih by default only sees ~3GB. Installing 64bit version of Ubuntu would help.
If you have 64bit OS it also could be a faulty RAM chip.

---

### Post by russlar on 2008-09-26
> **questionaire said:**
> I have 4 GB of RAM on my hp 8510p but Ubuntu only recognizes/utilizes 3GB.  Does anyone know why Ubuntu would not properly recognize the pre-installed RAM?  

I am fairly new to linux, so please keep the answers pretty basic if possible. 

Also, I am running 8.04

Can you open up Terminal and run uname -m, then post the output here?

---

### Post by prshah on 2008-09-26
> **questionaire said:**
> I have 4 GB of RAM on my hp 8510p but Ubuntu only recognizes/utilizes 3GB.  Does anyone know why Ubuntu would not properly recognize the pre-installed RAM?  


You're probably using the 32bit version, as mentioned earlier. (Incidentally, Windows will also see only 3Gb).

Here are your options:

a) Grin and bear it; 3Gb is plenty memory enough for Ubuntu.
b) Recompile your kernel to include PAE (Physical Address Extensions) support. Not recommended for newbie status.
c) Use 64 bit (amd64) iso. Not recommended for newbies.

All in all, I'd suggest (a).

---

### Post by ilrudie on 2008-09-26
> **prshah said:**
> You're probably using the 32bit version, as mentioned earlier. (Incidentally, Windows will also see only 3Gb).

Here are your options:

a) Grin and bear it; 3Gb is plenty memory enough for Ubuntu.
b) Recompile your kernel to include PAE (Physical Address Extensions) support. Not recommended for newbie status.
c) Use 64 bit (amd64) iso. Not recommended for newbies.

All in all, I'd suggest (a).

I'd suggest (c) before (a).  64-bit runs very smoothly and I don't think it was appreciably harder to install or configure.  There is also a good support community to get you going if you have trouble as well as plenty of tutorials out on the internet.

---


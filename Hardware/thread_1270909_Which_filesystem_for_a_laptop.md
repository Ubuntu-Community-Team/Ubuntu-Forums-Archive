---
title: "Which filesystem for a laptop?"
date: 2009-09-20
forum: Hardware
---

### Post by Nanthiel on 2009-09-20
Hello! 

I'm soon going to be installing Ubuntu on a new laptop, and I'd like to know which filesystem would be preferred?
(and how many partitions? I was thinking of a /, swap and a /home)

These are the specifications of it:
AMD Turion X2 Mobile RM76 2.3GHz 1MB L2
4GB DDR2 800MHz
500 GB SMART SATA2 5400 rpm
ATI Radeon Mobility HD4330 512MB/1024MB HyperM
(say if there are any other stats needed)


Thank you for your answers!

— Nanthiel

---

### Post by SlugSlug on 2009-09-20
> **Nanthiel said:**
> Hello! 

I'm soon going to be installing Ubuntu on a new laptop, and I'd like to know which filesystem would be preferred?
(and how many partitions? I was thinking of a /, swap and a /home)

These are the specifications of it:
AMD Turion X2 Mobile RM76 2.3GHz 1MB L2
4GB DDR2 800MHz
500 GB SMART SATA2 5400 rpm
ATI Radeon Mobility HD4330 512MB/1024MB HyperM
(say if there are any other stats needed)


Thank you for your answers!

— Nanthiel

if its 9.04 your installing then use ext4 

swap / & /home  is what I use.

---

### Post by Nanthiel on 2009-09-20
Okay, thanks! =)

I was thinking of using something else for /home, hearing that ext4 is not reliable. Is this true?

---

### Post by falconindy on 2009-09-20
> **Nanthiel said:**
> Okay, thanks! =)

I was thinking of using something else for /home, hearing that ext4 is not reliable. Is this true?
ext4 problems were hashed out and build notes for kernel 2.6.28 declare it to be stable. As with any file system (and hard drive), you should keep regular backups regardless.

---

### Post by Nanthiel on 2009-09-20
Okay great! Thanks for the replies! =)

---


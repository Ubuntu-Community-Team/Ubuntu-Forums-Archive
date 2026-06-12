---
title: "Ubuntu Detects 3.2gb out the 8gb I have installed"
date: 2010-01-09
forum: Hardware
---

### Post by Burky on 2010-01-09
I have ZT Affinity 7339ma in which I purchased 2 months ago. It has 8gb of DDR2 Memory. However it says in the System Monitor that I only have 3.2gb of memory. I am currently using Ubuntu Hardy Heron 8.04 (32bit). Anyone know how this could be?

---

### Post by jms1277 on 2010-01-09
its because you are running 32 bit if you want to use more than 3gigs of ram then you have to use 64 bit

---

### Post by Burky on 2010-01-09
> **jms1277 said:**
> its because you are running 32 bit if you want to use more than 3gigs of ram then you have to use 64 bit

It's impossible to have 8gb of RAM on 32bit?

---

### Post by jms1277 on 2010-01-09
yes you have to use the 64 bit there may be a work around try searching for it but the only way i know to get it recognize it is to run 64 bit

---

### Post by Burky on 2010-01-09
Dang bro that sucks.

---

### Post by underquark on 2010-01-09
32 bits just ain't enough to address all that RAM (8Gb is > 2^32) without workarounds.  Go 64-bit or sell some RAM (check your System Monitor - maybe you don't use even your 3.2Gb).

---

### Post by louieb on 2010-01-09
Might try the **linux-image-server **. Believe it has PAE (physical address extention) support. If so it sould be able to use all 8GB ram.

---

### Post by Burky on 2010-01-09
I'll just update to 64bit Linux Mint..

---


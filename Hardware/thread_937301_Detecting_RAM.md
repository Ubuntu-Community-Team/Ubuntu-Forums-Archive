---
title: "Detecting RAM"
date: 2008-10-03
forum: Hardware
---

### Post by gtno on 2008-10-03
I have 4 GB of ram installed on my computer and Windows Vista 32-bit detects all of it just fine.  However, in ubuntu only 2 GB of the ram is detected... is there away to fix this?

---

### Post by Sef on 2008-10-03
> I have 4 GB of ram installed on my computer and Windows Vista 32-bit detects all of it just fine. However, in ubuntu only 2 GB of the ram is detected... is there away to fix this?

1) Do you have 2 2gb sticks?

2) Make sure that the ram is properly seated.

---

### Post by gtno on 2008-10-03
Sorry, I should have specified.

I have 4x 1GB sticks of ram.

---

### Post by Yellow Pasque on 2008-10-04
Since you have 4GB of RAM, you should be running Ubuntu64.

---

### Post by gtno on 2008-10-04
> **Temüjin said:**
> Since you have 4GB of RAM, you should be running Ubuntu64.

Is there a way to upgrade from 32 bit to 64 bit?

---

### Post by shredder12 on 2008-10-04
> **Temüjin said:**
> Since you have 4GB of RAM, you should be running Ubuntu64.
Hey jst wanna know is it necessary to run Ubuntu 64 bit if one has 4GB RAM...coz i m not able to understand what's the problem with running Ubuntu 32 bit with a 4GB RAM

---

### Post by gtno on 2008-10-04
> **shredder12 said:**
> Hey jst wanna know is it necessary to run Ubuntu 64 bit if one has 4GB RAM...coz i m not able to understand what's the problem with running Ubuntu 32 bit with a 4GB RAM

The reason being is a 32 bit OS can't always allocate the memory due to the fact the way the system is designed, so it limited to how much ram it can actually read.  In windows vista 32 bit, I was able to tweak the system to read all 4 GB of ram and I am wondering if I can do that in Ubuntu.

---

### Post by Yellow Pasque on 2008-10-04
gtno, can you post the output of:
```
free -m
```

> Hey just wanna know is it necessary to run Ubuntu 64 bit if one has 4GB RAM
Why would you not run 64 bit Ubuntu if your processor is capable of it? It's not like you need to pay money for another version of the OS.

---

### Post by shredder12 on 2008-10-04
hey just curious to know..are there any advantages of a 64bit OS over 32 bit..??

---

### Post by Yellow Pasque on 2008-10-04
> **shredder12 said:**
> hey just curious to know..are there any advantages of a 64bit OS over 32 bit..??
Without launching into a dissertation on computer architecture: It's faster and can address a lot of memory.

---

### Post by gtno on 2008-10-04
Thanks for the help, but I just uninstalled and reinstalled a 64 bit system... it reads 3.8 GB of my ram now.

---


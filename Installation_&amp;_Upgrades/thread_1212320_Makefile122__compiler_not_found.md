---
title: "Makefile:122 *** compiler not found"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by InvisibleMan on 2009-07-13
I've been beating up this problem for a while, and it's winning.

I've installed Jaunty server on a machine where the network card isn't recognized. I downloaded the driver from Intel, unzipped it, and fired it up.
Problem: "make" not installed. Solution: install "make" from CD
Next problem: headers not installed. Solution: install build-essential and headers
Next problem: "Makefile:122 *** compiler not found" 

I'm stuck on this one. Any help out there?

---

### Post by lisati on 2009-07-13
Have you tried the following from the command line?
```
sudo apt-get install build-essential
```

---

### Post by InvisibleMan on 2009-07-14
Yes.

---


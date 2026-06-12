---
title: "Multiple processors and process IDs"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by nebc on 2006-07-10
Given a process ID how do I find out what processor it is running on?  I know how to look at all the fancy graphs and displays of the processor load, etc., but I couldn't find anything on this.

-NebC

---

### Post by nebc on 2006-07-10
I get to answer my own question!

apt-get install schedutils
man taskset

It is very very cool.

-Neb

---


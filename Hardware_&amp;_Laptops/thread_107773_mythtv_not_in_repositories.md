---
title: "mythtv not in repositories?"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by ionophore on 2005-12-23
Hey all, i was just working on trying to get my tv card to work and i notice that even though i have universe enabled, the mythtv package is not availavle.  All the guides that i've looked at for getting mythtv to work on ubuntu say to simply do an apt-get install mythtv, and yet, i'm not seeing it.

Am i missing something?

-ben

[PROBLEM SOLVED]

In case anyone in the future is wondering, i enabled "multverse" by appending the term "multiverse" to the universe listing in my /etc/apt/sources.list file.  Here are the relevant lines:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

---

### Post by ape on 2005-12-24
You've only added multiverse to your breezy-security updates.  You would also need to add multiverse to the following entry also (for breezy):

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy main restricted universe multiverse

---


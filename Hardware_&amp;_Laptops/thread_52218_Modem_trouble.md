---
title: "Modem trouble"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by factorof2 on 2005-07-27
I recently got my modem set up in Ubuntu but I'm having some problems using it.  The only way internet dependent applications seem to be able to communicate is when they're run as root through sudo su.  Could this be something to do with the root account being the only one able to access some modem functions?

---

### Post by jasmuz on 2005-07-27
Go to System -> Administration -> User & Groups, there allow your user to connect to the internet and add it to the DIP group.

---


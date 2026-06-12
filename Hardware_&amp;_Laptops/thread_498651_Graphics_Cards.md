---
title: "Graphics Cards"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by ErusGuleilmus on 2007-07-11
I recently bought a Nvidia to replace my ATI. When I swapped the two out, the xserver failed saying that there was no display device detected. It then reverts to command line interface. What is the solution to this?

---

### Post by xxchrisxx555 on 2007-07-11
you can try to run   "sudo dpkg-reconfigure xserver-xorg"

---

### Post by bren on 2007-07-11
you can run 

        sudo lshw

to check what (if anything) it does find

---


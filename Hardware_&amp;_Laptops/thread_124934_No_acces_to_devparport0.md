---
title: "No acces to /dev/parport0"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by rafarios on 2006-02-02
Hi, 
  I am trying to use pikdev or pkp (0.8.2).
  The installation doc says that I need ppdev module, and the /dev/parport0 .
 
 The ppdev module is installed (kernel 2.6.12-10) but I don't have /dev/parport0.
  So, I created it with: sudo mkmod /dev/parport0 c 99 0
  and then: sudo chmod 666 /dev/parport0

  Then when I use pkp it says:
     (/dev/parport0 must be rw enabled): No such device or address

  but when the permissions of /dev/parport0 are  rw-rw-rw-

  Any help ?

Thanks Forehand

---


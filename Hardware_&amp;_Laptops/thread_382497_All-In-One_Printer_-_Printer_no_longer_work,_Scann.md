---
title: "All-In-One Printer - Printer no longer work, Scanner does"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by Albinodrew on 2007-03-12
Hi everyone,

Recently I've encounter a small problem,
I have a All-in-one Printer (scanner, copier, printer) an Epson CX4800,
and I find myself with the following situation,

My printer is no longer recognize, but XSANE does recognize the scanner part, so after scratching my head for some time, on what could be the problem, it came to me to verify the permission for /dev/lp0 and /dev/usblp0, and there is was, Group for /dev/usblp0 was plugdev, so I changed it to lp (is it suppose to be plugdev?) 

So if that didn't happen to you, may I suggest to look at those permission, take note of then,
so if it does happen, you won't be in the dark like me and you will be able to eliminate that as the possible cause.

In hope you will never need this info.

Bye..

**Addendum:** The problem is due to a update of libgphoto2.

Bug #90724 [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/90724]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/90724")

---


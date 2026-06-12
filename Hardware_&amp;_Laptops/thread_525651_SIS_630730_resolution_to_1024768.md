---
title: "SIS 630/730 resolution to 1024*768"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by jlouwerse on 2007-08-14
Im trying to set the resolution of my videocard (SIS 630/730) to 1024*768 but it wont work. I know the videocard supports that resolution. Im quite new with ubuntu and i dont know where to start.

Thanx in advance.

J.

---

### Post by notoriousdbp on 2007-08-14
you might need to reconfigure your x server.  It's not as scary as it sounds.  Just open a terminal (Applications > Accessories > Terminal) and type

sudo dpkg-reconfigure xserver-xorg 

and just follow the steps through.  Let us know how you get on.

---


---
title: "[SOLVED] Is there a monitor control of hdd?"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by holihue on 2007-08-06
Is there a program to monitor all files that writes or reads from the HD?

It would be great to see how many programs that use the HD.

---

### Post by kidders on 2007-08-09
Hi there,

The answer to this question depends on what you want to do. For instance, your box can use libraries such as Gamin & FAM to keep itself informed of filesystem updates ... which is how applications like Nautilus & Konqueror know when to refresh their browser windows.

On the other hand, if you're simply interested in a snapshot of what your box is up to, "lsof" will enumerate all open file handles for you.

---

### Post by holihue on 2007-08-10
Thanks


I tried the lsof and it was something like what I want.

I did not install FAM, because I need to remove all the gnome apps.

---

### Post by kidders on 2007-08-10
Kewl. :-)

---


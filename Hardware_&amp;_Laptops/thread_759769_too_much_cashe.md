---
title: "too much cashe"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by wildman4god on 2008-04-19
does anyone out there know why my laptop is using 82% of 1 GB of memory for cashe. please help

---

### Post by the8thstar on 2008-04-19
Just to give my two cents, this is because Ubuntu manages memory differently than Windows would for instance.

AFAIK, it is normal to see a large amount of data being cached in memory to allow further use and faster access. Ubuntu should run just fine with 1Gb of RAM.

Tell me if this is a problem for you and we'll look into it together.

---

### Post by prshah on 2008-04-19
> **wildman4god said:**
> does anyone out there know why my laptop is using 82% of 1 GB of memory for cashe. please help

Using free memory for cache is a common tactic for smooth OS operation. It's done even in Windows, only not so transparently. The moment you need more memory for programs or data, the cache usage is reduced. 

It's nothing to worry about.

---

### Post by ibutho on 2008-04-19
The behaviour you describe is quite normal and nothing to worry about. The only time you should start worrying is if your system starts swapping a lot or slows down due to resource hogs. More information about how Linux manages memory is available at the [Gentoo Wiki]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management").

---


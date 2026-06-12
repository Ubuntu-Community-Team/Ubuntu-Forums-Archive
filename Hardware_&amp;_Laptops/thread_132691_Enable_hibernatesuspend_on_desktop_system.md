---
title: "Enable hibernate/suspend on desktop system"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by palomar on 2006-02-18
How do I enable hibernate or suspend on my desktop computer? On my laptop it works automatically (KLaptop), but with my desktop PC I can't find anything about hibernate/suspend.

I'm using Kubuntu 5.10.

---

### Post by KermitJr on 2006-02-18
Well, a quick search of hibernate in synaptic comes up with a package.

Personally, I would install KLaptop.  Then you'll be in familiar territory.

---

### Post by palomar on 2006-02-19
Well, I did have installed that package a few days ago, but it gives the following error:
```

rick@xp1800:~$ sudo hibernate
Password:
Your kernel does not have any recent Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://softwaresuspend.berlios.de/ for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.

```
I have no experience with 'compiling kernels' and when I look at that HOWTO it is lots of work. I think that is strange, because on my laptop hibernate worked directly 'out of the box' using KLaptop. Also Kubuntu 5.10.
So I already tried to start KLaptop. But, how do I start KLaptop? Adept package manager says it is installed (to be sure I reinstalled it), but I can't find any executable on my system.

---


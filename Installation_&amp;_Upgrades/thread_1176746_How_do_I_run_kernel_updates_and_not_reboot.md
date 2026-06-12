---
title: "How do I run kernel updates and not reboot?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by master5o1 on 2009-06-02
I have had my laptop on a suspend-resume cycle for eight days now, and realising that this contributes to my uptime I want to learn how to handle kernel updates and other reboot-required updates without requiring a reboot.

I have heard that it is possible here and am wondering how to do it.

I will check back in a few hours as I have to do something right now ;)

---

### Post by Mark Phelps on 2009-06-03
Since the kernel is loaded at boot time, updating the kernel would REQUIRE a reboot in order to load it.  Even if you kill off X and go to a console, you're still running the same kernel.  I don't see how you can switch kernels without a reboot -- but I'm willing to listen.

---

### Post by master5o1 on 2009-06-04
> **Mark Phelps said:**
> Since the kernel is loaded at boot time, updating the kernel would REQUIRE a reboot in order to load it.  Even if you kill off X and go to a console, you're still running the same kernel.  I don't see how you can switch kernels without a reboot -- but I'm willing to listen.

After some research I have found ksplice, ([http://www.ksplice.com/](http://www.ksplice.com/)).  I will probably not do anything about it :P

---

### Post by logos34 on 2009-06-04
> **master5o1 said:**
> After some research I have found ksplice, ([http://www.ksplice.com/](http://www.ksplice.com/)).  I will probably not do anything about it :P

hmm..interesting

---

### Post by grappler on 2009-06-28
Just did a smooth install of ksplice and it seems to work like a charm!
[http://www.ksplice.com/uptrack/download?now=y](http://www.ksplice.com/uptrack/download?now=y)

---


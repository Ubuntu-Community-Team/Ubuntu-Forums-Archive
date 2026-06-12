---
title: "Correct Version?"
date: 2008-08-31
forum: General Help
---

### Post by Jinkzt3r on 2008-08-31
So I use an Intel Pentium D CPU, does this mean I need to use the  Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)  or the 64bit AMD and Intel computer version?

---

### Post by InfinityCircuit on 2008-08-31
I believe that is an i686 architecture, meaning you should use x86 kernel and userland.  If you are curious about amd64 support, just do the following:

```
cat /proc/cpuinfo | grep lm
```

---

### Post by Taxman415a on 2008-08-31
Wikipedia says[1]  it has the x86-64 instruction set, so you could run the 64bit Ubuntu version if you wanted. They are also backwards compatible so you can run the usual Ubuntu as well.

[1] [http://en.wikipedia.org/wiki/Pentium_D](http://en.wikipedia.org/wiki/Pentium_D)

---

### Post by Jinkzt3r on 2008-08-31
> **Taxman415a said:**
> Wikipedia says[1]  it has the x86-64 instruction set, so you could run the 64bit Ubuntu version if you wanted. They are also backwards compatible so you can run the usual Ubuntu as well.

[1] [http://en.wikipedia.org/wiki/Pentium_D](http://en.wikipedia.org/wiki/Pentium_D)

Awesome, thanks for the help.

Love you two always :D

---


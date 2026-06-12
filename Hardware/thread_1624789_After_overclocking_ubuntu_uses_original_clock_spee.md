---
title: "After overclocking ubuntu uses original clock speed."
date: 2010-11-18
forum: Hardware
---

### Post by nagisa on 2010-11-18
It's my first time overclocking my CPU, because I noticed 720p to get stuck at some points when it needs more proccessing, so I want to add about 100-200MHz more to my AMD Athlon 64 3000+(stock clock - 1800MHz). I guess I correctly did that in bios(raised it from 200 to 220). And while rebooting it asked to press delete if it stucked @ overclocking, and it still loaded, so I guess it overclocked successfully.

Now the big problem comes up. Using all kinds of checking software : Perlmon, and "cat /proc/cpuinfo" Shows CPU clock to still be @ 1800MHz. What I should do for it to use 1980MHz(as in my calculations it should be)??

---

### Post by SlugSlug on 2010-11-18
are you able to see the speed at POST level?  I've try conform overclock first (either in BIOS or on POST screen) before using ubuntu

---

### Post by nagisa on 2010-11-18
Yes, I'm.
Well, I managed to make system use whole CPU by setting fixed K8 rate at 9 ( it was at auto ), but now I get this. Are there any way to make them work hand by hand?

---

### Post by SlugSlug on 2010-11-18
humm - is that CPU scaling ?

if it is then the system should use all Mhz as and when it's needed..?

---

### Post by nagisa on 2010-11-18
Well, thanks for help, I went across another thread where it's said that scaling uses percentage based scaling, and when CPU's overclocked it shows wrong details. I tested it with 720p again and it's not laggy anymore, so it's fixed.

---


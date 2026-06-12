---
title: "configuration flags used while compiling"
date: 2009-11-12
forum: Hardware
---

### Post by Albretch Mueller on 2009-11-12
How could I know the flags used for, say, the Open office configure script?

How is it that Open office and many other pieces of software seems to work functionally well under differing x86 hardware?

When you compile, do you compile to the hardware or the HAL?

Thank you
lbrtchx

---

### Post by Yellow Pasque on 2009-11-12
This usually works:
```
./configure --help
```

> When you compile, do you compile to the hardware or the HAL?
This doesn't make any sense to me :\

---

### Post by Albretch Mueller on 2009-11-13
I knew about "./configure –help" already

 OK, let me reword my question. When you install software in a regular way, the installation program usually checks the combination of hardware + operating system (+ software) in order to optimize its functionality, but when you use a liveCD this doesn't/can't happen, so my conclusion is software must be install in a "dumb"/baseline mode without any particular optimizations.

 Am I right? What is the art of this business?

 Thanks
 lbrtchx

---


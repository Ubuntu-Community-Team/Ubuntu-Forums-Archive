---
title: "[SOLVED] Compiling a 32 bit kernel on 64 bit machine"
date: 2008-11-13
forum: General Help
---

### Post by milasch on 2008-11-13
Hi...

I'm compiling a 32 bit kernel for my old laptop. Since it's old, it's taking a considerable time (p4m 1.8GHz). I have a Quad Core desktop which would do the job much faster... 

I figure I can simply copy the source and the .config file and run...
```

fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers

```
...to build it.

But i'm pretty sure I'd have to set some flags for the compiler in order to compile 32 bit... Does anyone know how to set these Environment vars or GCC flags?

Thanks

---

### Post by PatrickVogeli on 2008-11-13
maybe linux32 fakeroot make-kpkg bla bla bla would do the job?

---

### Post by milasch on 2008-11-13
To avoid problems I decided to install ubuntu 8.10 32bits on a flash drive, boot from it, and now I'm compiling the kernel.

Thanks!!!

---


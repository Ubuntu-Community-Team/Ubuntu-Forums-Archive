---
title: "Problems in Firefox or flash"
date: 2008-11-23
forum: General Help
---

### Post by aloasi on 2008-11-23
whenever i use firefox and enter youtube or sites that have flash inside my firefox becomes gray and my cpu is 50% loaded or more and i dont know why im using ubuntu 8.10 and i read about a bug with something called libflash i think. how can i solve this problem? Thank You

---

### Post by Izek on 2008-11-23
Flash interfaces becoming white or gray is normal under linux, especialy after a long period of time having your browser open. However, some people don't experience it like others do. For example, it takes mine about 3-4 hours for it to start doing this.

Flash also being high in cpu is normal as well, even in Windows, though in Windows, it usually takes more oomph for the cpu to run that high because of flash.

You'll probably be better off just waiting for flash to become, if ever, more stable for linux. I've gone through three versions already through linux (8, 9 and 10) and by far, 10 is the most stable of all of them, as 9 and 8 had crashes galore on youtube, whereas in flash 10, it barely had any, if at all.

---

### Post by aloasi on 2008-11-24
thank you for the info. So it is normal.

---

### Post by loomsen on 2008-11-24
> **aloasi said:**
> thank you for the info. So it is normal.

Not at all.

Depends on your arch (32bit - 64bit), if you use a wrapper, 32bits libs on 64 bit arch, which wrapper, which ia32libs if so and so on.

I have a 32bit-clean amd64 install, and don't experience any problems like this.

High CPU load is probably a conflict, either one I mentioned, or you have two different versions installed, or or or...

Try searching for libflash*.so.

I get this:
```

docter[~] locate libflas*.so
/usr/lib/opera/plugins/libflashplayer.so
/usr/share/opera/plugins/libflashplayer.so
docter[~] 

```

while one is a symlink pointing to the other one.

---


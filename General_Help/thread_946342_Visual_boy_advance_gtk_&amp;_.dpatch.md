---
title: "Visual boy advance gtk &amp; .dpatch"
date: 2008-10-13
forum: General Help
---

### Post by Kyosys on 2008-10-13
I am having the exact same problem described here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=452796](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=452796)


Basically, gameboy roms will always end in a segfault, no matter what I do. That bug report contains a .dpatch patch, which is supposed to fix this problem. In order to fix my problem, I tried applying the dpatch:
```
 dpatch apply Desktop/08_gvba_load_gb_rom.dpatch
```
but I got the following error:
```
/usr/bin/dpatch: line 939: dpkg-architecture: command not found
```

Could anyone tell me how to fix this please?

Thanks for your help

---


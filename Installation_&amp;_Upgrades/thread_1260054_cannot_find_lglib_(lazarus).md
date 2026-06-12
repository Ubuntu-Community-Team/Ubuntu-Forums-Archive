---
title: "cannot find lglib (lazarus)"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by demmanmc on 2009-09-07
I'm trying to use lazarus, i've succefully setup fpc, downloaded lazarus, then in terminal i used make, a long output ended with:
> Linking ../lazarus
> /usr/bin/ld: cannot find -lglib
> lazarus.pp(122,1) Error: Error while linking
> lazarus.pp(122,1) Fatal: There were 1 errors compiling module, stopping
> Fatal: Compilation aborted
> make[2]: *** [lazarus] Error 1
> make[2]: Leaving directory `/home/dc/Downloads/lazarus/ide'
> make[1]: *** [ide] Error 2
> make[1]: Leaving directory `/home/dc/Downloads/lazarus/ide'
> make: *** [ide] Error 2
Help please.

---

### Post by Partyboi2 on 2009-09-07
Try installing libgtk2.0-dev package if you have not already done so.
```
sudo apt-get install libgtk2.0-dev
```

---


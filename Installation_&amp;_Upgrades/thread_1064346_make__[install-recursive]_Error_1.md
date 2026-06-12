---
title: "make: *** [install-recursive] Error 1"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Declanthedork on 2009-02-08
So I was installing Kino, and I got this output.

```
libtool: link: unsupported hardcode properties
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[3]: *** [libtimfx.la] Error 1
make[3]: Leaving directory `/home/declan/Documents/Code/kino-1.3.3/src/timfx'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/declan/Documents/Code/kino-1.3.3/src/timfx'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/declan/Documents/Code/kino-1.3.3/src'
make: *** [install-recursive] Error 1


```

I snooped around (googled) the last line, and found that I need to install a compiler, such as g++. I installed g++ in Synaptic, but it still does the same thing. Thanks for any help.:KS

---

### Post by utnubuuser on 2009-02-08
gcc maybe?

---


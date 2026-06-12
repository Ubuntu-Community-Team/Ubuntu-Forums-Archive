---
title: "Liferea fails on libgnutls.so.13 after upgrade to intrepid"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by falafalaf on 2009-01-03
After upgrading from Hardy to Intrepid I get the following error when I try to start Liferea:```
/usr/local/bin/liferea-bin: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory

```Liferea verson 1.4.18-0ubuntu2, though I've tried 1.4.23, as well.  Does anyone know any fixes or workarounds?

---

### Post by falafalaf on 2009-01-04
I still haven't figured this out, but for anyone else who has this problem you can get your feed list from the Liferea configuration directory in your home directory where it is stored in the file feedlist.opml.  You can import your feeds from this file into other feed-readers.  I imported them into Akregator with no problems and my folder structure was even retained.

---


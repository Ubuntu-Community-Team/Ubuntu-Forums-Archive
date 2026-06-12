---
title: "Unable to upgrade due to unpacking error?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by rhcm123 on 2009-01-11
I was trying to upgrade the packages on my 8.04 server (it's headless, before you ask) and I encountered a slight problem:

This is the important part: (I'll post the rest if you want)
```
Unpacking replacement util-linux ...
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb (--unpack):
 unable to create `./usr/bin/fdformat': Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas on how to fix this?

---


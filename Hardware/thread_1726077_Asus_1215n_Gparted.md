---
title: "Asus 1215n Gparted"
date: 2011-04-10
forum: Hardware
---

### Post by surfingonmusic on 2011-04-10
so when i boot into the ubuntu live cd (10.10 desktop) and try to open gparted or disk utility it just crashes straight away! i can't edit my partitions at all

---

### Post by Yellow Pasque on 2011-04-10
Try starting from terminal:
```
gksu gparted
```

---

### Post by surfingonmusic on 2011-04-11
getting an error

glinmm - ERROR **:
unhandled exception (type std::exception) in signal handler
what: basic_string::_S_create

aborting...

that's the entire error

---

### Post by Yellow Pasque on 2011-04-11
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)

---


---
title: "will ubuntu use both cpu cores automatically"
date: 2008-06-13
forum: Hardware
---

### Post by timestoby on 2008-06-13
will ubuntu use both cores or will i have to download something in order to make use of both cores,thanks.

---

### Post by overdrank on 2008-06-14
> **timestoby said:**
> will ubuntu use both cores or will i have to download something in order to make use of both cores,thanks.

Hi and works great on both of my AMD X2 systems now and from the first installation.

---

### Post by housam on 2008-06-14
Type in the terminal the following code :
```
cat /proc/cpuinfo
```
You'll see your dual core detected and showed as cpu0 and cpu1 . they are working automatically.
also go for system >> admin. >> system monitor to see them working.

---

### Post by ikki_72 on 2008-06-14
> **timestoby said:**
> will ubuntu use both cores or will i have to download something in order to make use of both cores,thanks.

of course it will. since linux mainly used for servers, it supports multicore CPUs a long time ago.:popcorn:

---


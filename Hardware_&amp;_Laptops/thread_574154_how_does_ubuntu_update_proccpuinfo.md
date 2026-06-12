---
title: "how does ubuntu update /proc/cpuinfo"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by leond on 2007-10-12
How does ubuntu update /proc/cpuinfo ?  Where is the source code for that?:confused::confused:

---

### Post by Linicks on 2007-10-12
/proc  directory is a virtual directory - it is created (and all entries in it) from the Linux kernel of the current running state.

have a read of this:

[http://www.linuxjournal.com/article/8381](http://www.linuxjournal.com/article/8381)

Nick

---


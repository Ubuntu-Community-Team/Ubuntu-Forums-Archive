---
title: "SMP Kernel, Edgy Eft, Core2Duo 2.4, not booting SMP?"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by theskunk on 2006-11-03
so, i hear that we only use the one generic kernel now. Thats fine. 

But, why does my Core 2 Duo not show up as being multicore? im totally open to suggestions... and i'd rather know before i start the change to debian. 

Thanks!

---

### Post by po0f on 2006-11-03
theskunk,

Where are you getting that Ubuntu isn't running dual-core?  Post the out of:
```
$ cat /proc/cpuinfo | grep processor
```
If your results look like this:
```
processor        : 0
processor        : 1
```
Linux recognizes both cores.

---

### Post by theskunk on 2006-11-03
theskunk@MiniSkunk:~$ cat /proc/cpuinfo | grep processor
processor       : 0
theskunk@MiniSkunk:~$

---

### Post by theskunk on 2006-11-03
on no, i'm a moron. Due to old habits i went and straight for installing a new kernel. i installed a basic 386 one. im on the generic right now, and its all fixed. 

oops. thanks for the help though!

---

### Post by reazn on 2006-11-03
i did the same thing, installed a new kernel.. 
haha

---


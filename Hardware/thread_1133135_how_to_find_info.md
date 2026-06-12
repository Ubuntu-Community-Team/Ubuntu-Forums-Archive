---
title: "how to find info?"
date: 2009-04-22
forum: Hardware
---

### Post by JakeHinojosa on 2009-04-22
how do i find my hardware info? like processor, memory, etc

?

---

### Post by coffeecat on 2009-04-22
Terminal:

```
lshw
```

---

### Post by docetrago on 2009-04-22
> **JakeHinojosa said:**
> how do i find my hardware info? like processor, memory, etc

?

You must type in the console ( command line ) :

sudo lshw

This provides a comprehensive listing of all your hardware.

Cheers !

---

### Post by rainwalker on 2009-04-22
Also, instead of looking in a terminal, you can install the "sysinfo" program, which will give you a nice, organized GUI for checking everything.

---

### Post by cariboo on 2009-04-23
You could also install lshw-gtk, for a gui version of lshw. It is in the repositories, and you use Add/Remove Programs or Synaptic Package Manager to install it.

---


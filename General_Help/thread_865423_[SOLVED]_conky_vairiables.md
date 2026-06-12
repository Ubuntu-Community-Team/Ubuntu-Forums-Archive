---
title: "[SOLVED] conky vairiables"
date: 2008-07-20
forum: General Help
---

### Post by tad1073 on 2008-07-20
what is the "grep" varialble that displays the processor type i.e "Pentium III (Coppermine)

---

### Post by easybake on 2008-07-20
```
cat /proc/cpuinfo
```

you can run that with an execi variable. But it also lists a whole lot more info than you're probably looking for.

---

### Post by DaymItzJack on 2008-07-20
```
cat /proc/cpuinfo | grep "model name"
```

?

---

### Post by tad1073 on 2008-07-21
sorry, not the one I am looking for.

bump

---

### Post by easybake on 2008-07-22
> **tad1073 said:**
> sorry, not the one I am looking for.

bump

What are you really looking for? Also if you already know the answer why 'grep' for it.

---


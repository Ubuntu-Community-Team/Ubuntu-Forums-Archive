---
title: "New kernel headers?"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by Spif on 2005-01-23
I need new kernel headers for my kernel 2.6.8.1-3-386. Tried sudo apt-get install kernel-headers-2.6.8-3-386 but there was no match. 

Can anybody help me?

---

### Post by runenes on 2005-01-23
if you type 
```

sudo apt-get install kernel-headers

```

you'll see the candidates available for installation, oddly enough I didn't see 2.6.8 headers when I ran the command...

---

### Post by Spif on 2005-01-23
[QUOTE=runenes] oddly enough I didn't see 2.6.8 headers when I ran the command...[/QUOTE]

Same problem here :sad:

---

### Post by az on 2005-01-23
linux-headers-2.6.8.1-3-386

Kernel-headers are debian, linux-headers are Ubuntu.

---

### Post by Spif on 2005-01-23
[QUOTE=azz]linux-headers-2.6.8.1-3-386

Kernel-headers are debian, linux-headers are Ubuntu.[/QUOTE]

Thanks! :D

---


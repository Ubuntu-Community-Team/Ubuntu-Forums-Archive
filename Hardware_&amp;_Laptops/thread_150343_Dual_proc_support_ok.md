---
title: "Dual proc support ok?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by Xeno.God.Of.Death on 2006-03-25
how is the dual proc support on ubuntu?


EDIT: sorry, i should have mentioned that i am asking about the support for a dual P3 1ghz setup.

---

### Post by Iandefor on 2006-03-25
It's fine. There's the SMP kernel, which I think Ubuntu should detect automatically.
Install Ubuntu, open up a terminal and run ```
uname -r
``` to find out if you have the SMP kernel installed- it'll have "smp" somewhere in the name. If you don't... report back for more instruction :).

---

### Post by Xeno.God.Of.Death on 2006-03-25
will do. thank you.

---

### Post by taurus on 2006-03-25
Sorry but Ubuntu will install a generic i386 kernel whether you have dual processor or 10 processors!!!  However, you can use synaptic to install the smp kernel after your system reboots or finishes installing...

---

### Post by taurus on 2006-03-25
Sorry but Ubuntu will install a generic i386 kernel whether you have dual processor or 10 processors!!!  However, you can use synaptic to install the smp kernel after your system reboots or finishes installing...

---


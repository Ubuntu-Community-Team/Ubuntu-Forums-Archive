---
title: "problem with temperature on laptop or maybe not?"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by przemek.kom on 2007-09-22
Hi,

On my laptop ASUS X51R, when I do: acpi -V I've got information:

```
Thermal 1: critical , 52.0 degrees C
AC Adapter 1: on-line
```

Temperature is OK (always was like this). I dont' remember is later was "critical" or "ok", but when I touch laptop it's not so hot. Fan is working. Max temp. was 57 degrees C

I don't know... does "critical" mean that there is a problem? or I shouldn't worry about it.

---

### Post by anemptygun on 2007-09-22
An easy way to find out the maximum temperature your processor can support without burning out is referring to the table given at [http://users.erols.com/chare/elec.htm](http://users.erols.com/chare/elec.htm). This table shows that Pentium 4 processors can operate up to 75º C (167º F) or slightly less, depending on the model,  Athlon 64 can run up to 65º C or 70º C (149º F or 158º F), depending on the model, Athlon XP processors can run up to 85º C or 90º C (185º F or 194º F), also depending on their clock, and Sempron processors can run up to 90º C (194º F). So from what this tells me I'm not too worried.

---

### Post by przemek.kom on 2007-09-22
I don't worry about temp, beacuse i think it is normal, but I'm worry about "Thermal 1: critical".I don't know what it mean.

---

### Post by anemptygun on 2007-09-22
> **przemek.kom said:**
> I don't worry about temp, beacuse i think it is normal, but I'm worry about "Thermal 1: critical".I don't know what it mean.

Hmm, I'm not sure. The way I interpret it is that Thermal 1: is a critical component?

I would try it out but I don't have the acpi command.

---

### Post by przemek.kom on 2007-09-22
"Thermal 1: critical" - I think that is "thermal 1" state.

On other forums I saw listing form acpi -V:

"Thermal 1: ok"

---

### Post by anemptygun on 2007-10-10
Well.... :-k

---


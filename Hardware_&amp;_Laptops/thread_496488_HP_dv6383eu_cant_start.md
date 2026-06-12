---
title: "HP dv6383eu cant start"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by straps on 2007-07-09
Hi all, I have an HP dv6383eu (AMT Turion 64 x2, 2Gb RAM, 160GB hd, Vista preloaded) and I want to install Ubuntu Linux Feisty on it.

When I boot the live cd, it stops after writing "Starting GDM (Gnome Desktop Manager)" and It does not respond to any Input (CTRL+ALT+Canc, CTRL+ALT+F1, ecc...)
I've tried with "Secure Graphics Mode" too, with same results.

The only think I can do is Power Off it...

Can you help me please...I don't want Vista, thanks

---

### Post by EXCiD3 on 2007-07-09
Ok, which video card do you have? If its one of the newer Nvidia 8000 series then that might be your problem.

---

### Post by straps on 2007-07-10
It's an nVidia GeForce GO 7200

thanks for reply

---

### Post by przemyslaw on 2007-07-10
boot from command line 

```
noapic nolapic
```

---

### Post by straps on 2007-07-10
I'll try, thanks

---


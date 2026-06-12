---
title: "Kernel 2.6.14.2 - linux-headers"
date: 2005-11-22
forum: General Help
---

### Post by Sebby on 2005-11-22
I've just compiled a new kernel using the latest from kernel.org (due to problems with rebooting and shutdown). How do I install linux-headers for this kernel version though? I'm sure I can't do it through Synaptic... :confused:

---

### Post by ranf on 2005-11-22
[QUOTE=Sebby]I've just compiled a new kernel using the latest from kernel.org (due to problems with rebooting and shutdown). How do I install linux-headers for this kernel version though?[/QUOTE]
You have the full source. Why do you want the headers seperatly?

You can `make-kpkg kernel_headers'.

---

### Post by Sebby on 2005-11-22
[QUOTE=ranf]You have the full source. Why do you want the headers seperatly?

You can `make-kpkg kernel_headers'.[/QUOTE]
The answer to that question is I don't know...

I'm new to Linux... That's the only explanation I can give! :p

---


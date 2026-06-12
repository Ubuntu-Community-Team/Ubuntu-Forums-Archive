---
title: "find wireless card"
date: 2011-11-16
forum: Hardware
---

### Post by ntesla123 on 2011-11-16
How do I find which wireless card my computer has?

---

### Post by nosmadar on 2011-11-16
Open a terminal session and try this  It will produce a lot of output but the " | more" will let you page through it. So you can see what's what.

lspci -vnbG | more

---


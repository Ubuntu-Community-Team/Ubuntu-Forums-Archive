---
title: "Enabling Hyperthreading in Gutsy"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by LavianoTS386 on 2007-11-06
Hi I have an Intel Pentium 4 3.2ghz that has hyper-threading capability. After enabling HT in the bios and editing the grub boot list to include "ht=on" I still don't see my processor shown as two when I look into the hardware information applet.

What gives?

---

### Post by dgar on 2007-11-06
> **LavianoTS386 said:**
> Hi I have an Intel Pentium 4 3.2ghz that has hyper-threading capability. After enabling HT in the bios and editing the grub boot list to include "ht=on" I still don't see my processor shown as two when I look into the hardware information applet.

What gives?

Try 'cat /proc/cpuinfo'.

Scroll up a bit.  See if there is a CPU0 and a CPU1.  If not, make sure there is a ' ht ' in the capabilities list.

---

### Post by LavianoTS386 on 2007-11-06
Oh okay there is CPU 0 & CPU1. It just doesn't show up that way in Hardware Information, so I should be fine then, right?

---


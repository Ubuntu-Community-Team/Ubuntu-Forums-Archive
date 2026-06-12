---
title: "Guidance-power-manager problems"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by JimFlint on 2007-05-12
Hi,
I am experiencing crashes of guidance-power-manager.
I have recently install feisty onto two different machines
a) AMD-64 in an ABit mobo using an nVidia 6600
b) AMD Opteron with an nVidia FX1400
They both give a crash dialog saying it caused a signal 11 (SIGSEGV)
Whilst this is annoying, the main problem is that when I select "Monitor & Display" in  System Settings - it also crashes; meaning that I cannot set up my displays properly.

I see many people are having a similar problem, but have not seen a solution - does anyone know if there is a solution or workaround.

ps. I tried removing kde-guidance-powermanager - this stopped the start-up crash report but I was still unable to get into the display settings.

---

### Post by BjoernVDM on 2007-07-11
just a hint: this is caused by xrandr crashing. Try running xrandr on the command line and you will see it.

A driver problem?

---


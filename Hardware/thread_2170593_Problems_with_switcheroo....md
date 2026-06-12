---
title: "Problems with switcheroo..."
date: 2013-08-26
forum: Hardware
---

### Post by gvraziel77 on 2013-08-26
Hi guys, i've got a problem with my graphic card. So, i've a notebook, with switchable graphics. Firstly, i've used proprietary drivers, but these make mouse laggy in games (only with discrete graphics). So i've decided to try again radeon drivers, but when i use switcheroo nothing happens: using the graphical version, ubuntu says it's changing graphic card, but when i use *cat* to read values in switch file (/sys/kernel/debug/vgaswitcheroo/switch) i find written that the intel is still working... indeed, nothing happens on the screen. It seems Ubuntu is unable to modify the file. I've tried to write the permission into rc.local file, too. Any idea? Anyway, i've succeed in turning on the ati (so it receives power). And sorry for the bad english, i read it a lot but i don't speak or write it very often!

---


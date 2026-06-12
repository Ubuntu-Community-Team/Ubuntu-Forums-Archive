---
title: "Computer throttling because of IRQ?"
date: 2011-05-21
forum: Hardware
---

### Post by Freek07 on 2011-05-21
Sometimes when I use USB devices, vmware or even some async web apps (upload few youtube videos simultaneously), computer becomes choppy with low cpu usage, low LA, free ram (top) and no disk utilization (iostat).

Performance gets really low (if I click a line in gEdit it takes 2-3 seconds for cursor to get there!).

HW is ok- the temperatures are OK, voltages are OK.

I'm suspecting interrupts are firing too rapidly. Is there any way to tell it- to monitor IRQ rate? Is there a way to limit IRQ rate?

---


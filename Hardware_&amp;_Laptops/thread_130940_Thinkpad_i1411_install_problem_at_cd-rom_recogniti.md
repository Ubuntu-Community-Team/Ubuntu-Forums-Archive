---
title: "Thinkpad i1411 install problem at cd-rom recognition stage"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by idenr on 2006-02-15
The Thinkpd i1411 is a P2 with 96 meg 4 gig circa 1998. The installation script hangs when it gets to the part about installing devices to recognize the cd-rom drive. It hangs on cd-ide. The dmesg output (obtained from the shell called up by pressing Alt+F2 during installation for those of you newbies reading this looking for helpful tips) shows that the script can tell it is a Sanyo CDR-372B firmware 1.24. Then it polls IRQ 15 and says "nobody cared" and advised to try the install with the irqpoll option. Doing this results in the word "Ready." being displayed and then nothing happening (system "freeze" or "hang"). I'm at a loss to know what to try.

---

### Post by Greg2 on 2006-02-15
[QUOTE=idenr]Then it polls IRQ 15 and says "nobody cared" and advised to try the install with the irqpoll option. Doing this results in the word "Ready." being displayed and then nothing happening (system "freeze" or "hang").[/QUOTE]
Try this:```
irqpoll routeirq
```

---

### Post by mpvano on 2006-02-15
I had to also disable dma during the install on my 1400 - if I remember correctly that was an option in the boot menu.

Mario

---

### Post by idenr on 2006-02-17
Thank you for the help. It took me past the cd-rom recognition point.

Now I ran "live irqpoll routeirq noapic nolapic"

It hangs at "Loading additional components" "Retrieving libnss-files-udeb" and the Alt+F2 terminal can not be raised.

Also when I ran "live irqpoll routeirq" it stopped when it got to "Preparing for live session" at the "Configuring language..." stage.

So it seems to hang at different points in the boot process at different times.

---

### Post by Greg2 on 2006-02-17
[QUOTE=idenr]Now I ran "live irqpoll routeirq noapic nolapic"[/QUOTE]
Why are you using ‘live’ as a boot parameter? Don’t you want to install it? :-k

---

### Post by idenr on 2006-02-17
Since I am having difficulty installing anyway I wanted to make sure I can run ubuntu before re-partitioning the machine and potentially leaving it stalled midway unuseable and then needing to install something else if the ubuntu won't work - so I wanted to try it out with the live cd first to make sure it can actually run on the machine.

---


---
title: "IRQ woes, please help."
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-04-25
I recently upgraded to feisty and had problems with my nvidia card and a very long boot time due to time outs on sata/pata. It turns out that the cause of both my woes is that the host bridge and video card are sharing the same interrupts. When I do a lspci -v I seen them both on 00:00.0. This can be sort of solved by adding IRQPOLL to the grub boot, but that gives me choppy GL, but does remove the long timeout on start up.

Is there anyway of changing the assignments? Do I have to go fishing in my bios and guess the irq assignment there? What irq is 00:00.0 ?

I am no hardware buff so be nice.

--edit---

found that my video is sharing an irq 11, how do I change that?

---


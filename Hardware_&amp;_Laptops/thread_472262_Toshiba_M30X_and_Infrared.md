---
title: "Toshiba M30X and Infrared"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by pgargate on 2007-06-12
Hello,

I'm totally new to Linux, and although curious about it, I,m finding it extremely hard to configure.
Laptop is a Toshiba M30X-128 (Portugal) and I'm running Feisty.

most of the hardware is working, but I can seem to understand how to turn IR on. Research on internet advises irda-utils toshset smsc-ircc, etc...

I have irda-utils and toshset installed, but can't understand how to make smc-ircc work.

IRDA help says
"
Run it as root:
	$ ./toshsat1800-irdasetup 

then you can install the smc-ircc module:
	$ modprobe smc-ircc

I've noticed that the smc-ircc needs parameters ircc_sir and ircc_fir to be specified. So you'd probably add:

	options smc-ircc ircc_dma=3 ircc_irq=7 ircc_cfg=0x2e ircc_sir=0x2e8 ircc_fir=0x2f8

to /etc/modules.conf
"
but when i run modprobe smc-ircc I get "module smc_ircc not found" (don't know why it changes the slash to underscore)

I also can't find the file modules.conf Apparently I don have it and don't know where to look for it.

I'm not sure if I'm doing something wrong or forgetting something. Does anyone know how to configure the infrared, or at least make this modules work?
(please... in a very clear language... I hardly understand linux... Even compiling seems too hard, with constant errors and libraries missing...)

Thank you,

Pedro

---

### Post by pgargate on 2007-06-14
Somebody could help please?

---


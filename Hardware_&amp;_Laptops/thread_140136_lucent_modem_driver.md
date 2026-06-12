---
title: "lucent modem driver"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by fazee on 2006-03-05
hi 

 i am new to ubuntu using it for the first time. i have lucent modem and running well on windows xp now i want to use it on ubuntu but now driver by defualt 

 kindly any body help me 

thnx and regards 
faisal iqbal ch 
lahore pakistan

---

### Post by gborzi on 2006-03-05
I have a Lucent winmodem on my laptop too, lspci reports
0000:02:04.0 Communication controller: Lucent Microelectronics LT WinModem (rev 02)
I put it on work using a prepackaged driver for kernel 2.6.12-10-686 from
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/)
If you have a different kernel (e.g. 2.6.12-10-k7) then you'll need to recompile it.

---

### Post by towsonu2003 on 2006-03-05
check out the second link in my signature (for more information on winmodems and configuration etc etc).

---

### Post by threegremlins on 2006-11-23
Don't know if this helps, but after following the links and doing what they said, Efax wouldn't work. I nventually figured out to get efax working I had to change ttys1 to ttyLTM0 in efax settings to get it working.

---


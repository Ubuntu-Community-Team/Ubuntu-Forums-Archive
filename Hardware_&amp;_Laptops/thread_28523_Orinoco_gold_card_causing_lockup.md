---
title: "Orinoco gold card causing lockup"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by MightyPez on 2005-04-20
Ok, scouring the forums and the internet as a whole have yielded nothing in this department, so I'll come out and ask. 

I'm running an HP Pavillion ze4600 (Athlonxp 2500+, ATI IGP northbridge) and every time I plug in my Orinoco gold classic wifi PCMCIA card, it hard locks the system. This only happens in linux. I've tried live CD's like Knoppix and it happens there too.

It also hard locks during the install if I leave the card in there. When it's scanning the hardware, it hard locks on the "enabling PC Card services" portion. I've tried flashing the nic it to an older version, 6.02, and the newest 8.7.

---

### Post by mendicant on 2005-04-21
Do you happen to know if it works on other laptops?

---

### Post by MightyPez on 2005-04-21
[QUOTE=mendicant]Do you happen to know if it works on other laptops?[/QUOTE]

I'm not sure with Ubuntu. I know that the card *did* work on an old Compaq Presario I had using Knoppix-STD.

---

### Post by rjhale3629 on 2005-04-30
Letme see if I can remember - The pcmcia card is taking up the same irq as your touchpad and causes the latop to lock up. You need to make changes to the config.opts file. I've got a compaq 2100 and an orinoco gold classic card. 
--------------------------------------------------------------------------------------
Here is my config.opts file: 
#include port 0x100-0x4ff
#include port 0x800-0x8ff
#include port 0xc00-0xcff
#include memory 0xc0000-0xfffff
#include memory 0xa0000000-0xa0ffffff
#include memory 0x60000000-0x60ffffff

include port 0xfd00-0xfdff, port 0xfc00-0xfcff
include memory 0x80000000-0x80000fff, memory 0xffeff000-0xffefffff
include memory 0xfbeff000-0xffefefff, memory 0x000d7000-0x000d7fff

# High port numbers do not always work...
# include port 0x1000-0x17ff

# Extra port range for IBM Token Ring
include port 0xa00-0xaff

# Resources we should not use, even if they appear to be available

# First built-in serial port
#exclude irq 4
# Second built-in serial port
#exclude irq 3
# First built-in parallel port
#exclude irq 7
exclude irq 1
exclude irq 2
exclude irq 3
exclude irq 4
exclude irq 5
exclude irq 6
exclude irq 7
exclude irq 8
exclude irq 9
exclude irq 10
exclude irq 11
exclude irq 12
#exclude irq 13
exclude irq 14
exclude irq 15
---------------------------------------------------------------------

---


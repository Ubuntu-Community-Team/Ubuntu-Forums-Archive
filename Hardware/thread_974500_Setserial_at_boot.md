---
title: "Setserial at boot?"
date: 2008-11-07
forum: Hardware
---

### Post by AndrewWalker on 2008-11-07
I've almost got my ir port to work but I need to do the equivalent of 

sudo setserial /dev/ttyS1 uart none
modprobe lirc_sir irq=3 io=0x02f8

at boot up.
Anyone know how I go about doing this and which script to edit?

---


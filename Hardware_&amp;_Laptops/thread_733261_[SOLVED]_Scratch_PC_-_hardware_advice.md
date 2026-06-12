---
title: "[SOLVED] Scratch PC - hardware advice"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Jeztastic on 2008-03-23
Hi

I got given a PIII 733mhz machine with no HDD, RAM or PCI cards. 

I have some PC100 RAM from an old PII machine - is it likely to be a problem if I put PC100 RAM in with the PIII chip? I suspect that it's meant to be P133.

Equally, will the graphics and network cards transfer to the new PC OK?

I am planning to set up the PIII as a network server :)

---

### Post by keratos on 2008-03-23
Might help if you tell us what graphics and network manufacturer and model , the cards are ... mightn't it.

as regards RAM, CPUs access RAM includes "wait states" where the CPU waits a number of clock cycles if RAM isn't ready to accept/provide data. While this waiting is going on, the CPU does nothing (to be a bit simplistic) Thus, if your RAM is slower that the recommended speed, your CPU will just "insert" more wait states ... i.e. system is slower. For file server situations, this isnt going to be a problem given that the much slower Hard Disk devices are the bottleneck, not the CPU.

---

### Post by Jeztastic on 2008-03-24
Thanks keratos, that was really helpful. Am now up and running and typing this from an Xubuntu server box! Just got to iron out a few minor problems now...

BTW. I would have given you more info on the hardware, I just wanted to know if the clock speed problem worked in the same way for PCI cards, but the graphics card is running fine.

---

### Post by keratos on 2008-03-25
> **Jeztastic said:**
> Thanks keratos, that was really helpful. Am now up and running and typing this from an Xubuntu server box! Just got to iron out a few minor problems now...

BTW. I would have given you more info on the hardware, I just wanted to know if the clock speed problem worked in the same way for PCI cards, but the graphics card is running fine.

good, welcome and have a many a pleasant late nights burning the candles :popcorn:

in regard to the wait states and all that, I did omit to say that this is usually configurable in the BIOS becuase, sometimes, just sometimes the manufacturers brand their memory at a certain speed but we all know thats just marketing hype and we can OVERCLOCK

oh yeah!!

okay, well, have a good time and good luck with the server.

---


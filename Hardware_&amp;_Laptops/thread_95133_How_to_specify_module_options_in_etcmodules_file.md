---
title: "How to specify module options in /etc/modules file?"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by sb73542 on 2005-11-25
Hi, 

I have an IBM Thinkpad 600, running Breezy.  The old ISA soundcard works, but it's not autodetected.  I have to manually "modprobe snd-cs4236 port=0x530 cport=0x538 irq=5 dma1=1 dma2=0 isapnp=0" to get it running.  How can I automate this for every bootup?  I know I can add modules into /etc/modules, but what about all the module options?

Thanks a lot!

---

### Post by Lambert on 2005-11-25
They can be added right after adding the module name, just keep it all on the same line (don't hit return)

---

### Post by sb73542 on 2005-11-25
[QUOTE=Lambert]They can be added right after adding the module name, just keep it all on the same line (don't hit return)[/QUOTE]


Huh, that's easy enough, isn't it?  Thanks!  :D

---


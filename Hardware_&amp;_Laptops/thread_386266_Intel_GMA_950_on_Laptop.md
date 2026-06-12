---
title: "Intel GMA 950 on Laptop"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by tk623 on 2007-03-16
Everytime i start Ubuntu on my laptop (hp dv5237cl)  I am left with these errors on tty1.  Everything seems to be working well, with the exception of my s-video port and my VGA port.  I know these are related but I'm not sure how to fix it.  The graphics card is an Intel 945.  I would like to be able to have different images on the external screen then on my built in screen, but even if they just mirror everything, I could live with that.  I really just want to get it to work.

I'm using Ubuntu 6.10.

Any help is greatly appreciated.  



Part of dmesg

```
[17179570.820000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.820000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.820000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.820000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.820000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.820000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.820000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[17179579.312000] Cannot allocate resource for EISA slot 1
[17179579.312000] Cannot allocate resource for EISA slot 2
```

Matching Sections of lspci 
```

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Unknown (5)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Unknown (5)

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: 8a000000-8a0fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Unknown (5)



```

---

### Post by tk623 on 2007-03-19
WOW - threads sink fast here, I'm already 13 pages deep after only 2 days.

Can anyone offer some help?

I've been searching the forums and have been unable to find any help.

---


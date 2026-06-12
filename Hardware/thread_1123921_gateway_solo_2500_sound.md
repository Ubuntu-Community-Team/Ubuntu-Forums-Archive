---
title: "gateway solo 2500 sound"
date: 2009-04-12
forum: Hardware
---

### Post by velodyne1 on 2009-04-12
I have gateway solo 2500 laptop, ( 2.6.27-11-generic) having problems with sound.  module snd-cs4232 installs successfully.  No combination of irqs or parameters work.  lspnp -v yields:

00:03 NMX2210 (unknown)
    state = active
	dma 0
	dma 1
	irq 5
	io 0x220-0x22f
	io 0x530-0x537
	io 0x388-0x38f
	io 0x330-0x331
	io 0x370-0x371

00:04 NMX2220 (unknown)
    state = active
	io 0x201-0x201

has anyone been able to get sound to work on this laptop?

---

### Post by acimmarusti on 2009-04-12
Don't know much, but this might help you:

[http://www.thehayesweb.org/jhayes/solo2500.html](http://www.thehayesweb.org/jhayes/solo2500.html)

and this:

[http://linux-laptops.blogspot.com/](http://linux-laptops.blogspot.com/)

In both cases it appears to work fine.

---

### Post by velodyne1 on 2009-04-13
tried all those first

---


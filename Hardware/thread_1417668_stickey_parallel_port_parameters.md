---
title: "stickey parallel port parameters"
date: 2010-02-27
forum: Hardware
---

### Post by jfarrug on 2010-02-27
I have a dual boot system (windosxp and ubuntu ver 9.1) where the motherboard does not provide a parallel port. I purchased a pci to parallel port card in order to run my parallel port zip250 drive. This works fine under windows xp but ubuntu does not see the port or the zip drive
When i run the command
sudo llspci -v 
it results in
08:00.0 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03) 
	Subsystem: Device a000:2000 
	Flags: bus master, medium devsel, latency 64, IRQ 15 
	I/O ports at ec00 [size=8] 
	I/O ports at e880 [size=8] 
	Memory at fbeff000 (32-bit, non-prefetchable) [size=4K] 
	Memory at fbefe000 (32-bit, non-prefetchable) [size=4K] 
	Capabilities: [48] Power Management version 2 

but zip drive is  not seen by the system but when i run

sudo  modprobe parport_pc io=0xec00,0xdd00 irq=15

Ubuntu then sees the zip drive and every thing works ok. The problem is that when i reboot i have to do it all over again. How do i make the change in port parameters stick?

---


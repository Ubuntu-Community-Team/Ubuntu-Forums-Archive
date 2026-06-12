---
title: "parallel port on expansion card is not detected"
date: 2014-09-27
forum: Hardware
---

### Post by marun2 on 2014-09-27
i have PCI expansion card with parallel port and some serial ports
i want to connect my printer (laserjrt 6l, on another port works fine) to it, but system is not detecting that parallel port
here [http://www.asix.com.tw/FrootAttach/driver/MCS98xx_Linux_Driver_Installation_Guide_v100.pdf](http://www.asix.com.tw/FrootAttach/driver/MCS98xx_Linux_Driver_Installation_Guide_v100.pdf) is guide to configure parport_pc but it only confuses parport_pc and there appears some /dev/lp* but noone is working
i need this card because my new MB don't have parallel port
my system is ubuntu 14.04 3.13.0-37
i attached log when reloading lp ppdev parport_serial parport_pc parport without aditional arguments

---

### Post by marun2 on 2014-09-28
**SOLVED **i read some notes in source code of parport_pc.c ```
Note that the ECP registers may not start at offset 0x400 for PCI cards, but rather will start at port->base_hi.
``` so i changed io addres to 0xc400 and to a **free IRQ** (in my case 22) and it started working

but there is still parport on addres 0xc800 but this is a fake

---

### Post by marun2 on 2014-09-28
OK not solved at all

on my another PC there is not working even my integreted parport and addresses reported in lspci are different too
```
02:00.0 Communication controller: MosChip Semiconductor Technology Ltd. PCI 9845 Multi-I/O Controller (rev 01) (prog-if 02)	Subsystem: LSI Logic / Symbios Logic 1P4S (1 Parallel / 4 16550A Serial Port Adapter)
	Flags: medium devsel, IRQ 21
	I/O ports at d050 [size=8]
	I/O ports at d040 [size=8]
	I/O ports at d030 [size=8]
	I/O ports at d020 [size=8]
	I/O ports at d010 [size=8]
	I/O ports at d000 [size=16]
	Kernel driver in use: parport_serial



```

---


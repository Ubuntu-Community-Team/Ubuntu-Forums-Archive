---
title: "cannot install ubuntu driver for a serial pci card"
date: 2013-01-12
forum: Hardware
---

### Post by vincent_kelly on 2013-01-12
Hi all,

I want to use a LMS211 Laser scanner connected to an industrial computer through a serial PCI card [DSC-200/300](http://www.ieci.com.au/products/Product_Page2.asp?Product_ID=7#). This card provides RS422 ports for the communication with the laser scanner. 

The computer runs Lubuntu 12.04. This PCI card is not recognized by the kernel (3.2.0-35). 

Here is the list of the serial ports:

results of ```
$lspci -vv
```

```
02:0d.0 Multiport serial controller: Quatech Inc Device 01b1 (rev 01)
	Subsystem: Quatech Inc Device 01b1
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e8021000 (32-bit, non-prefetchable) [size=128]
	Region 1: I/O ports at d100 [size=128]
	Region 2: I/O ports at d200 [size=16]
	Capabilities: <access denied>
```

results of ```
$sudo setserial -g /dev/ttyS*

```
```
acm@acm-robucar:~$ sudo setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 10
/dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 5
/dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0
```

ttyS0-ttyS3 are the serial ports(RS232) originally on the computer. 
ttyS4-ttyS5 are the PCI serial ports(RS422). 

I tried to install a driver for this PCI card.
I downloaded the driver from [here](http://www.bb-elec.com/getattachment/33a08b1c-e430-4e1a-9d4c-29caf7e600bf/serial-QTPCI-1-27-tar.gz.aspx). It was developed for (Fedora FC2 and Suse 9.1 - 2.6 kernel). 

According to the readme file, I put the installation files under /usr/serqt_pci/.  There was some compile errors when run 'make' due to the change of kernel. I was able to resolve that. But 'make install' doesn't work. It runs a file ./startup in the folder. There's some kernel folders that's located differently in Ubuntu (like in fedora it's /etc/rc.d/rc0.d/, in ubuntu it's /etc/rc0.d/). I changed some but was not sure about all of them.

After 'make install', the port is still not working. 
Can anyone provide any insight on this? I've attached a zipped file of this driver installation folder with this post. 

Thanks!  
Vincent

PS: Below is what i got after 'make install':

```
acm@acm-robucar:/usr/serqt_pci$ dmesg | grep ttyS
[    0.287668] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.376777] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.420743] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.504409] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    0.546090] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.632763] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.672590] 00:09: ttyS2 at I/O 0x3e8 (irq = 10) is a 16550A
[    0.756811] 00:0a: ttyS3 at I/O 0x2e8 (irq = 5) is a 16550A
[10441.930971] serial8250: ttyS4 at I/O 0xd200 (irq = 19) is a 16550A
[10441.933798] SerQT_PCI:  register_serial() at 0xd200,irq 19, ttyS4 succeded
[10441.955841] serial8250: ttyS5 at I/O 0xd208 (irq = 19) is a 16550A
[10441.958320] SerQT_PCI:  register_serial() at 0xd208,irq 19, ttyS5 succeded
```

```
acm@acm-robucar:/usr/serqt_pci$ sudo setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 10
/dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 5
/dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS4, UART: 16550A, Port: 0xd200, IRQ: 19
/dev/ttyS5, UART: 16550A, Port: 0xd208, IRQ: 19
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0
```



```
lspci -vv
```
```
02:0d.0 Multiport serial controller: Quatech Inc Device 01b1 (rev 01)
	Subsystem: Quatech Inc Device 01b1
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e8021000 (32-bit, non-prefetchable) [size=128]
	Region 1: I/O ports at d100 [size=128]
	Region 2: I/O ports at d200 [size=16]
	Capabilities: <access denied>

```

```
sudo lspci -vv
```

```
02:0d.0 Multiport serial controller: Quatech Inc Device 01b1 (rev 01)
	Subsystem: Quatech Inc Device 01b1
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e8021000 (32-bit, non-prefetchable) [size=128]
	Region 1: I/O ports at d100 [size=128]
	Region 2: I/O ports at d200 [size=16]
	Capabilities: [40] Power Management version 1
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] CompactPCI hot-swap <?>
	Capabilities: [4c] Vital Product Data
		Unknown small resource type 0b, will not decode more.

```

---


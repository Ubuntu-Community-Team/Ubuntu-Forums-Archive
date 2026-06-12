---
title: "Enable More than 4 serial ports"
date: 2011-05-09
forum: Hardware
---

### Post by rplankenhorn on 2011-05-09
I have a PC/104 form factor board that has 4 COM ports on it and I also have a PC/104 power supply connected to the PCI bus that also has a UART controller on it with two COM ports.  If I disable two of ports on the computer board, the two serial ports from the power supply show up and are assigned /dev/ttyS2 and /dev/ttyS3 but if I enable all four ports on the computer board, they don't show up.  Here is the output from dmesg:

```

[    0.769193] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.769374] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.769549] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.769716] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.769892] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    0.770423] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.770698] 00:09: ttyS1 at I/O 0x2f8 (irq = 0) is a 16550A
[    0.770971] 00:0a: ttyS2 at I/O 0x3e8 (irq = 3) is a 16550A
[    0.771244] 00:0b: ttyS3 at I/O 0x2e8 (irq = 0) is a 16550A
[    0.771430]   alloc irq_desc for 19 on node -1
[    0.771437]   alloc kstat_irqs on node -1
[    0.771455] serial 0000:02:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.771488] Couldn't register serial port 0000:02:04.0: -28

```

Output from lspci for the power supply UART:

```


02:04.0 Serial controller: Exar Corp. XR17C/D152 Dual PCI UART (rev 02) (prog-if 02 [16550])
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at dffff800 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: serial


```

---

### Post by imjustmatthew on 2012-01-26
Digging up an older thread, but this was a top result on Google for this problem.

What's happening is that the Debian kernel is compiled by default with only 4 serial ports enabled. See [http://www.debian-administration.org/users/lauri/weblog/1]("http://www.debian-administration.org/users/lauri/weblog/1") **The hard way** to fix this would be to recompile, changing the config parameters:
```
CONFIG_SERIAL_8250_NR_UARTS=32 
CONFIG_SERIAL_8250_RUNTIME_UARTS=4
```
Recompiling would let you set the parameters in the kernel itself (and maybe have more than 32 serial ports?).

**The easy way** to fix this is (as root) to edit /etc/default/grub and append " 8250.nr_uarts=8" (without quotes) to the end of the line "GRUB_CMDLINE_LINUX_DEFAULT=". It might then look like :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet 8250.nr_uarts=8"
```
You can set any number up to 32 as the number of serial ports this way.

You then have to run "update-grub" as root. After rebooting you should have the serial ports working.

---


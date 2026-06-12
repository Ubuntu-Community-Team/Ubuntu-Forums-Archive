---
title: "Adding Parallel Port Devices to parport_pc"
date: 2006-02-10
forum: Hardware &amp; Laptops
---

### Post by Scrambler on 2006-02-10
Hello,

I am trying to connect parport_pc driver to two parallel port interfaces on a PCI card. So I figured (from my PCI list) that I can simply load my parport_pc module with the following options:

```
parport_pc io=0x378,0x9c00,oxa000 irq=7,none,none
```

but alas, this does not work. So I've checked that parport_pc is loading /dev/parport0 properly, which it does. My printer is detected and the io address is actually 0x378

```
Feb 10 10:49:29 localhost kernel: [4296258.658000] pnp: Device 00:09 activated.
Feb 10 10:49:29 localhost kernel: [4296258.658000] parport: PnPBIOS parport detected.
Feb 10 10:49:29 localhost kernel: [4296258.658000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Feb 10 10:49:29 localhost kernel: [4296258.661000] parport0: Printer, Hewlett-Packard OfficeJet Series 600
Feb 10 10:49:29 localhost kernel: [4296258.675000] ppdev: user-space parallel port driver
```

But if I try to add the parport_pc modules by stating io=0x378, I get an error saying

```

Feb 10 10:51:18 localhost kernel: [4296367.870000] parport 0x378 (WARNING): CTR: wrote 0x0c, read 0xff
Feb 10 10:51:18 localhost kernel: [4296367.870000] parport 0x378 (WARNING): DATA: wrote 0xaa, read 0xff
Feb 10 10:51:18 localhost kernel: [4296367.870000] parport 0x378: You gave this address, but there is probably no parallel port there!
Feb 10 10:51:18 localhost kernel: [4296367.870000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]

```

Can anybody help me to get the module options right?

Thanks in advance,

     Scrambler

---


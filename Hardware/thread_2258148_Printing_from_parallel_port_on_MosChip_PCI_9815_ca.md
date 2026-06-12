---
title: "Printing from parallel port on MosChip PCI 9815 card"
date: 2014-12-25
forum: Hardware
---

### Post by novotnyw on 2014-12-25
Hello,

running Xubuntu 14.04 i386 (32 bit) with kernel 3.16.0-28-generic, I have problem getting output from parallel port on this PCI card:

```

05:00.0 Communication controller: MosChip Semiconductor Technology Ltd. PCI 9815 Multi-I/O Controller (rev 01)
    Subsystem: LSI Logic / Symbios Logic 2P0S (2 port parallel adaptor)
    Flags: medium devsel, IRQ 17
    I/O ports at d050 [size=8]
    I/O ports at d040 [size=8]
    I/O ports at d030 [size=8]
    I/O ports at d020 [size=8]
    I/O ports at d010 [size=8]
    I/O ports at d000 [size=16]
    Kernel driver in use: parport_pc

```

it is dual LPT extending card. The card is recognized properly and there are automatically created two parport and lp devices:

```

[    8.881895] parport_pc 00:06: reported by Plug and Play ACPI
[    8.881940] parport0: PC-style at 0x378, irq 5 [PCSPP]
[    8.976817] lp0: using parport0 (interrupt-driven).
[    8.977231] parport1: PC-style at 0xd050 (0xd040), irq 17, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[    9.192393] parport1: Printer, Canon BJC-250
[    9.219178] lp1: using parport1 (interrupt-driven).
[    9.219263] parport2: PC-style at 0xd030 (0xd020), irq 17, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[    9.304262] lp2: using parport2 (interrupt-driven).

```

parport0 is onboard parallel port, which works great, parport1 and parport2 are parallel ports on MosChip 9815 PCI card, which I have problem with.

I need to attach and use two LPT printers with my computer, one is dot matrix Epson printer and second is ink printer Canon BJC-250. When I connect these printers to onboard parport0, i can print to them from command line with no problem, but I was unable to print to them from parport1 and parport2 even, as you can see, the printer is recognized as attachet to parport1. I was able to install the printer in CUPS, but it simply don't prints anything.

This PCI card works with these printers on Windows, so it is linux issue, I think it might be wrong LPT mode or some linux kernel bug, but I'm not very experienced in LPT nor in linux kernel so I can only search for similar issues on the internet and I slowly run out of usefull results.

Any advice appreciated.

---

### Post by novotnyw on 2014-12-25
Again I find out, that put problem "on the paper" will help me solve it. As I read my post again, I have realized, that output of dmesg (second code block) writes two io addresses for parport1 and parport2 (second address in parentheses). I have such theory, that the first address was used for input and the second address for output, therefor the printer was detected, but no output was printed.

I manually overriden setting of parport. Firstly unload all parallel port related drivers:
```

rmmod lp
rmmod ppdev
rmmod parport_serial
rmmod parport_pc
rmmod parport

```

Then I load all these drivers again and set parport_pc manually to use only one address for each port (not the one in parentheses):
```

modprobe parport
modprobe parport_pc io=0x378,0xd050,0xd030 irq=5,17,17
modprobe parport_serial
modprobe ppdev
modprobe lp

```

after that, my lp1 started to print successfully. To make this settings permanent, I created text file:
/etc/modprobe.d/parport.conf
```

# content of /etc/modprobe.d/parport.conf
options parport_pc io=0x378,0xd050,0xd030 irq=5,17,17

```

and voila, after restart all my printers works as I needed.

The only drawback is, that dmesg now tells me, that IRQ 17 is already in use, so the device falls to polled operation
```

[    8.574512] parport0: PC-style at 0x378, irq 5 [PCSPP]
[    8.663490] parport1: PC-style at 0xd050, irq 17 [PCSPP,TRISTATE,EPP]
[    8.663496] parport1: irq 17 in use, resorting to polled operation
[    8.943052] parport1: Printer, Canon BJC-250
[    8.943575] parport2: PC-style at 0xd030, irq 17 [PCSPP,TRISTATE,EPP]
[    8.943580] parport2: irq 17 in use, resorting to polled operation
[    9.036532] lp0: using parport0 (interrupt-driven).
[    9.036557] lp1: using parport1 (polling).
[    9.036577] lp2: using parport2 (polling).

```

but I can live with that :)

---


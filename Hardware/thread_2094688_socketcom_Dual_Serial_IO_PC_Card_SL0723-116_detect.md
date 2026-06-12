---
title: "socketcom Dual Serial I/O PC Card SL0723-116 detected wrong"
date: 2012-12-14
forum: Hardware
---

### Post by cheinrici on 2012-12-14
Hello guys

I want to use my socketcom Dual Serial I/O PC Card SL0723-116 (ruggedized, PCMCIA, datasheet can be found at [http://www.socketserial.com/support/Cards/CFandPC%20Card%20Datasheet.pdf](http://www.socketserial.com/support/Cards/CFandPC%20Card%20Datasheet.pdf)) on ubuntu 12.04.

When I plug it into the slot, the kernel detects it, but
[LIST=1]
[*]only one port
[*]even this one port does not work (assumed: com settings wrong)
[/LIST]

Here's the output of dmesg:
```

[  340.513911] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[  510.344104] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[  510.344622] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
[  510.346484] serial_cs 0.0: trying to set up [0x0104:0x00a1] (pfc: 0, multi: 0, quirk: f9604b68)
[  510.386670] ttyS0: detected caps 00000700 should be 00000500
[  510.386687] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16C950/954

```

Can anybody help how to configure the card correctly?

---


---
title: "PCMCIA serial port card problem"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by rogerzzhang on 2007-12-02
I can't get my PCMCIA dual serial port card work under ubuntu 7.10.

The card is made by ARGOSY. dmesg shows

```

[ 5447.636000] pccard: PCMCIA card inserted into slot 0
[ 5447.636000] pcmcia: registering new device pcmcia0.0
[ 5447.684000] parport_cs: parport_pc_probe_port() at 0x83e8, irq 3 failed

```

It is a serial port card, why does system load parport_cs instead?

pccardctl ident shows:

```

Socket 0:
  product info: "PCMCIA", "RS-COM 2P", "", ""
  function: 3 (parallel)

```

---


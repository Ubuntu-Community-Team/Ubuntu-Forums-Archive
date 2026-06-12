---
title: "Firewire &amp; DuoConnect"
date: 2010-08-29
forum: Hardware
---

### Post by asearle on 2010-08-29
Hi Everyone,

I have an Adaptec DuoConnect PCMCIA card (AUA-1411) which handles both USB and Firewire.  Under Windows both work fine but under Ubuntu only the USB ports work.

I have a second laptop with a mini Firewire port which also doesn't seem to be able to handle Firewire (under Ubunut).

My question is whether there is an issue with Ubuntu and PCMCIA and/or Firewire?

At first I thought it might be an issue of the powering of the drive but now I am experimenting with an externally powered drive (which works under exactly the same constellation under Windows) so this is not the case.

Anyway, I would welcome any tips that you can give me.

Many thanks,
Alan Searle

---

### Post by IcarusR on 2010-08-29
There are no issues with either PCMCIA cards or firewire in Ubuntu 10.04.
I have PCMCIA modem, NIC, WIFI & Firewire card all work well, modem & wifi need drivers.

Is the card recognised by Ubuntu, does it show when you type in a terminal

```
lspci
```

Is there any mention of the card in the logs, eject it wait a minute then insert it. Now in a terminal type 

```
dmesg
```

Near the end you should see something like this

```
[108218.216964] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[108218.217043] pci 0000:08:00.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[108218.217056] pci 0000:08:00.0: reg 14 io port: [0x00-0x7f]
[108218.217069] pci 0000:08:00.0: reg 18 32bit mmio: [0x000000-0x0000ff]
[108218.217145] pci 0000:08:00.0: supports D2
[108218.217148] pci 0000:08:00.0: PME# supported from D2 D3hot D3cold
[108218.217155] pci 0000:08:00.0: PME# disabled
[108218.217294] ohci1394 0000:08:00.0: enabling device (0080 -> 0083)
[108218.217304] ohci1394 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[108218.217315] ohci1394 0000:08:00.0: setting latency timer to 64
[108218.275113] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[88000000-880007ff]  Max Packet=[1024]  IR/IT contexts=[4/8]
[108219.552431] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0011066600000b30]

```

I also have a mini firewire port that I use to connect my old ipod.

---


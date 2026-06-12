---
title: "Ubuntu 13.10 - PCI Parallel card not recognized"
date: 2014-04-06
forum: Hardware
---

### Post by shay-zukerman on 2014-04-06
Hi everybody,

Due to historical reasons, I had to purchase a Parallel PCI card, whose main goal was attaching a Parallel Security dongle to it so a Window 98 VM could recognize and use.

As the VM did not recognize the port, I connected a printer to the port (yes, I still have all the legacy hardware ...).
Unfortunately, Cups did not locate the printer so I realized that things are bad in lower level.

I did lot of Google-ing but no help, so here I am, and I hope you can assist me.

As far as i understand now, the source of the issue is that the card is disabled.
This was clarified from the card's details in lspci -vvv:

01:01.0 Parallel controller: Device 1c00:2170 (rev 0f) (prog-if 01 [BiDir])
        Subsystem: Device 1c00:2170
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 7
        Region 0: I/O ports at c880 [**disabled**] [size=8]
        Region 1: I/O ports at c800 [**disabled**] [size=8]

The card, which was bought at "Ali-Express" arrived with a drivers mini-CD, which includes a directory for Linux device drivers, but I could not be 100% what is the correct one.
The card seems to be based on a chip made by "WCH GROUP".

My questions:


[LIST=1]
[*]How can the above I/O ports be enabled?
[*]Is there an official driver for that card?
[/LIST]

Thanks for your help!!

Shay

---

### Post by web-stephen on 2014-04-24
I'm at a similar stage - I have a "CH35" PCI parallel card from "WCH".  Strangely, "lspci -v" gives  "using serial kernel driver"

I have a dual-boot Windows / Ubuntu 14.04 system - and can print from Windows OK

I've tried adding a parport driver using

 sudo modprobe -r lp
 sudo modprobe -r parport_pc
 sudo modprobe parport_pc io=0xbe00 irq=none
 sudo modprobe lp

then

 ls /proc/sys/dev/parport

gives parport0 in addition to "default"

but after that, no joy - even the "serial printer" options in "system settings - add printer" disappear

the WCH CD drivers include various "makefiles" so I guess I need to go in deeper. Is this PCI card so strange that standard drivers don't work?

---

### Post by shay-zukerman on 2014-05-02
Hi,
At least the card is active under Windows - as actually I need it for a Win 98 Vm.

Thanks for that!

Shay

---


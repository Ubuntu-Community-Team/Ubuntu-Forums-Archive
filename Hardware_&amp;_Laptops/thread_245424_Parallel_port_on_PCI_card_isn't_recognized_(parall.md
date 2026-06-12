---
title: "Parallel port on PCI card isn't recognized (parallel/serial ports combo)"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by mildred on 2006-08-27
Hi,

Recently, I bought a PCI card with 2 serial ports and one parallel port because my motherboard doesn't have any of these ports and because my printer is using a parallel port.

The device is seen on [this web site]("http://perso.orange.fr/connectic/cpsq.htm").

The problem, the card is well recognized (the 2 serial ports works well as ttyS4 and ttyS5), my 56K modem is well-recognized.

But, the parallel port associated with the card does not work and isn't recognized by the system. When I open the hardware manager, I can see the PCI card recognized and below the two serial ports, but no parallel port.

I also tested with the Ubuntu 4.10 live CD and the parallel port is recognized. I coudn't make CUPS working on the live CD (so I couldn't print some documents) but the following command printed "test" on the printer :
```
echo "test" > /dev/lp0
```

Some lspci informations :
```
$ lspci -v -d 1409:7168
0000:00:0c.0 Serial controller: Timedia Technology Co Ltd PCI2S550 (Dual 16550 UART) (rev 01) (prog-if 02 [16550])
        Subsystem: Timedia Technology Co Ltd: Unknown device 5079
        Flags: stepping, medium devsel, IRQ 169
        I/O ports at 9000 [size=32]
        I/O ports at 9400 [size=8]
        I/O ports at 9800 [size=8]


```

Some screenshoots of the device manager : [http://mildred632.free.fr/persistant/2006-08-28-0233/]("http://mildred632.free.fr/persistant/2006-08-28-0233/")

---

### Post by wr0x2 on 2006-08-28
4.10? Is that a typo? Try a newer version of ubuntu if that is what you're using, 6.06 is reputed to have better hardware support than previous versions.

If that's only the livecd version and your main system is up to date, then sorry, I have no idea.

---

### Post by mildred on 2006-08-28
No :) I said that the card worked withthe 4.10 live-cd which was the first release of Ubuntu but actually I work with the Dapper 6.06 (it is my main OS) but it does not work.

So, because it worked with ubuntu 4.10 I know it is not a hardware problem and also that linux kernel should have a driver for this card.

Thanks for the answer

---


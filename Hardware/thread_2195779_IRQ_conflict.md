---
title: "IRQ conflict"
date: 2013-12-26
forum: Hardware
---

### Post by filozofwiejski on 2013-12-26
Hello all,
my notebook - Samsung N130 ( [http://www.samsung.com/pl/consumer/pc-peripherals-prtinters/ultra-mobile-pc/pc-archives/NP-N130-KA01PL](http://www.samsung.com/pl/consumer/pc-peripherals-prtinters/ultra-mobile-pc/pc-archives/NP-N130-KA01PL) ), during startup, throw error 
> ERROR
Resouce Confilict - PCI Network Controller on Motherboard
Bus:03, Device:00, Function:00
How view IRQ device list? how change default IRQ device? and how fix it :p?

---

### Post by tgalati4 on 2013-12-26
There is a debug switch in *irqbalance* that might give more information.

tgalati4@Mint14-Extensa ~ $ apropos irq
irqbalance (1)       - distribute hardware interrupts across processors on a multiprocessor system

Does your wired network port work?

Does your network card show up in *lspci*?

Open a terminal:

```
 lspci | grep Network
```

---

### Post by filozofwiejski on 2013-12-26
*irqbalance *showed nothing. My wireless card not working (wireless menager isn't showed card). 
> marcin@marcin-N130:~$  lspci | grep Network
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


---

### Post by tgalati4 on 2013-12-26
What is the output of:

```
sudo irqbalance --debug
```

And the output of:

```
lspci
```

Search the forums for: Atheros AR9285

Try this suggestion:

[http://ubuntuforums.org/showthread.php?t=2194703&highlight=Atheros+AR9285](http://ubuntuforums.org/showthread.php?t=2194703&highlight=Atheros+AR9285)

---

### Post by filozofwiejski on 2013-12-27
Output irqbalance and lspci (I don't write in forum, because I exceed post limit): [http://freetexthost.com/0ujosypf6h](http://freetexthost.com/0ujosypf6h)
I read [http://ubuntuforums.org/showthread.php?t=2194703&highlight=Atheros+AR9285](http://ubuntuforums.org/showthread.php?t=2194703&highlight=Atheros+AR9285) soon.

---


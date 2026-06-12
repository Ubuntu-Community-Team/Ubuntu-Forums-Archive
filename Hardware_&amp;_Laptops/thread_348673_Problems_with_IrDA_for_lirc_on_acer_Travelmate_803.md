---
title: "Problems with IrDA for lirc on acer Travelmate 803LCi"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by andrea.tagliasacchi on 2007-01-29
HI there, i was attracted by the possibility of controlling my kde applications with a remote and i started looking around for IrDA support offered by lirc.

First of all Is there any way of understanding looking at dmesg if the IRDA device has been associated to a /dev/SOMETHING?

Since i have an acer travelmate 803 and i tried to follow this [guide]("http://gentoo-wiki.com/Gentoo_Acer_Travelmate_803LCi_Manual#IRDA_support") but nothing seems to work. I enabled the IR component from bios and I installed these IRDA related packages: [INDENT]**irda-utils, kdelirc, lirlircclient0, lirc, setserial**
[/INDENT]The guide suggested to turn off uart with the command:[INDENT]**sudo setserial /dev/ttyS1 uart none**[/INDENT]( Why? what is uart? ) 

then to execute the command: [INDENT][B]sudo modprobe nsc-ircc io=0x2f8 irq=3 dma=1
[/B][/INDENT]for which i receive the following error message:[INDENT]**FATAL: Error inserting nsc_ircc (/lib/modules/2.6.17-10-generic/kernel/drivers/net/irda/nsc-ircc.ko): No such device**
[/INDENT]How am i supposed to correct this error?

I checked at any of these steps if** irdadump** gave any output but i get no output at all.

I tried to search for other tutorials / guides but with any luck..
From [this page ]("http://homepages.fh-giessen.de/%7Ehg13418/gentoo/803lci_thread/acer_803_lci_system_report.html")I found out that my IRDA is a IrDA-schneller infrarotanschluss that doesn't say anything to me.


I hope some of you with an ACER laptop had IrDA and lirc successfully installed and that you could give me a hand with this since i am completely lost.

Thanks

---

### Post by papiesh on 2008-07-07
```
sudo setserial /dev/ttyS1 uart none port 0 irq 0; 
modprobe --ignore-install nsc-ircc dongle_id=0x09 io=0x2f8 irq=3 dma=3 
i'm not sure dma , try dma=1 also
```

---

### Post by papiesh on 2008-07-07
After that if irdadump still give nothing, try this trick 
```
echo 1 > cat /proc/sys/net/irda/discovery
```
:guitar:

---


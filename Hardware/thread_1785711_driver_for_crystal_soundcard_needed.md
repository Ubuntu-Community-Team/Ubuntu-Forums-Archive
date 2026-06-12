---
title: "driver for crystal soundcard needed"
date: 2011-06-18
forum: Hardware
---

### Post by Total Noob on 2011-06-18
I have xubuntu relating to ubuntu 9.4, but no driver for the crystal soundcard inside. The computer is an IBM Thinkpad 600e with a celeron 400 and 256 mb ram.

How do I get the driver and get it going? Thanks.

---

### Post by Toz on 2011-06-18
Here are instructions from a launchpad bug report on getting it to work: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/40116/comments/22]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/40116/comments/22")

---

### Post by Yellow Pasque on 2011-06-18
You already have the driver; it's a matter of telling Ubuntu to use it. The directions are straightforward, copy+paste style.
The only thing left out is how to open a file with root permissions:
```
sudo mousepad <file>
```

---

### Post by tgalati4 on 2011-06-18
Those old crystal sound cards used the ISA bus (before PCI became popular) and the linux kernel dropped support for the ISA bus so you have to manually load a few modules to get it to work.

For instance on a Dell Optiplex GX1 (500 MHz Pentium III), has a Crystal Sound 4236 chip:

408       Module snd-cs4236
409       -----------------
410     
411         Module for sound cards based on CS4235/CS4236/CS4236B/CS4237B/
412                                        CS4238B/CS4239 ISA chips.
413     
414         isapnp      - ISA PnP detection - 0 = disable, 1 = enable (default)
415     
416         with isapnp=0, the following options are available:
417     
418         port        - port # for CS4236 chip (PnP setup - 0x534)
419         cport       - control port # for CS4236 chip (PnP setup - 0x120,0x210,0xf00)
420         mpu_port    - port # for MPU-401 UART (PnP setup - 0x300), -1 = disable
421         fm_port     - FM port # for CS4236 chip (PnP setup - 0x388), -1 = disable
422         irq         - IRQ # for CS4236 chip (5,7,9,11,12,15)
423         mpu_irq     - IRQ # for MPU-401 UART (9,11,12,15)
424         dma1        - first DMA # for CS4236 chip (0,1,3)
425         dma2        - second DMA # for CS4236 chip (0,1,3), -1 = disable
426         
427         This module supports multiple cards. This module does not support autoprobe
428         (if ISA PnP is not used) thus main port and control port must be
429         specified!!! Other ports are optional.
430     
431         The power-management is supported.

----------------------------------------

ALSA Dell GX1 Sound card notes
Minty4 (based on Gutsy)
Settings:  snd-cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 dma1=1 dma2=0

So you can test it manually by doing:

sudo modprobe cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 dma1=1 dma2=0

If that works then put cs4236 in /etc/modules and modify /etc/modprobe.d/alsa-base with the rest of the parameters.

To help with finding the correct switches, search for your specific chip in google and use one of the several alsa tools available to test your sound card:

apt-cache search alsa

sudo apt-get install alsa-base alsa-utils

man asoundconf

And if I read the link above, it just repeated exactly what I said.:)

---


---
title: "Silicom PEG2BPI driver for Foscal"
date: 2020-06-26
forum: Hardware
---

### Post by albertcuy on 2020-06-26
Hi All,

Foscal seems to be detecting it as e1000 NICs. i tried compiling from source(from Silicom's FTP site) but i'm getting stumped at the "This driver is not supported on kernel versions older than 2.4.0" error message.

Are there drivers available on Foscal for this card? If not, what was the latest distribution that still supported this ?

tia

---

### Post by Yellow Pasque on 2020-06-26
Does the e1000 module not work? This card uses an Intel chipset, so I would guess that's the correct module you need.

---

### Post by albertcuy on 2020-06-28
Hi,

Yes, it is being detected as such, and the module e1000.o is loaded...but the card/ports don't work. The activity LEDs are also off.

The card is a two-port Silicom with Bypass function. i read somewhere that i need the e1000**bp**.o  driver/module

---

### Post by Yellow Pasque on 2020-06-28
THere's a report of it working on 16.04:
[https://www.joshcurry.co.uk/posts/using-a-silicom-dual-port-copper-ethernet-pci-e-intel-based-bypass-server-adapter-pe2g2bpi-on-ubuntu-16-04/](https://www.joshcurry.co.uk/posts/using-a-silicom-dual-port-copper-ethernet-pci-e-intel-based-bypass-server-adapter-pe2g2bpi-on-ubuntu-16-04/)

I was not able to get e1000bpe to build under 20.04 VM. I was able to hack around a few issues with the Makefile, but the driver is simply too old for kernel 5.4 as it is. Maybe it would be simple enough to update it for someone familiar with kernel development, but that is not me. I suggest trying to contact the company and see if they'll actually update their drivers. This is what happens with out of tree modules..

---


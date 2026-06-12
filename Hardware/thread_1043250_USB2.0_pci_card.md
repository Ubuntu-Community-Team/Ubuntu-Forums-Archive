---
title: "USB2.0 pci card"
date: 2009-01-18
forum: Hardware
---

### Post by eckeroo on 2009-01-18
Hello,

I am trying to ascertain the degree of support Ubuntu can provide USB PCI controller cards. My motherboard is an ASUS A7M-266 with only USB1.1 capability. I'm assuming a USB2.0 PCI will work and provide me with USB2.0 data rates.

Unfortunately, only the Belkin models of USB2.0 PCI cards seem to be commonly available to me in the UK. These products do not mention any driver support for Linux. This is also the case for the Maplin brand of USB2.0 PCI cards.

The Belkin products in particular are:

Belkin 3-Port USB 2.0 PCI Card (F5U219VEA1)

Belkin 5-Port USB 2.0 PCI Card (F5U220VEA1)

Having given the UBUNTU forums a thorough going over with search keywords including USB, USB2.0 and USB2.0 PCI - I've come across two significant threads:

[http://ubuntuforums.org/showthread.php?p=3209619](http://ubuntuforums.org/showthread.php?p=3209619)

The originator of this thread found that his Rosewill RC-101 USB card was recognised by Ubuntu. Unfortunately this card is not available in the UK market.

[http://ubuntuforums.org/showthread.php?t=867870](http://ubuntuforums.org/showthread.php?t=867870)

The originator of this thread was enquiring about the possibility of installing a USB2.0 PCI card, but failed to announce if he was successful or not.

I was unsuccessful in searching the wiki pages for information on controller card support. It only had a section on the old serial ports (as opposed to USB ports) - [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/) - further searches from the links there proved fruitless.

I would like to know what USB2.0 PCI cards will work on Ubuntu and if they require ndiswrapper to work.

Regards

---

### Post by nick09 on 2009-01-18
You can get this one here:
[http://www.provantage.com/encore-software-enlusb2-5pci-br~7ENCR1LE.htm](http://www.provantage.com/encore-software-enlusb2-5pci-br~7ENCR1LE.htm)

You don't need to worry about drivers as it's a Plug-n-Play card.

---

### Post by eckeroo on 2009-01-18
>  You can get this one here:
[http://www.provantage.com/encore-sof...r~7ENCR1LE.htm](http://www.provantage.com/encore-sof...r~7ENCR1LE.htm)

I'm afraid that shop is in the USA and I'm in the UK.

> You don't need to worry about drivers as it's a Plug-n-Play card. 

If Ubuntu can run any or most Plug-n-Play devices, could you please give me a reference where that is stated?

Regards

---

### Post by nick09 on 2009-01-18
They do ship to the UK:
[http://www.provantage.com/international-orders~xintl.htm](http://www.provantage.com/international-orders~xintl.htm)

Well I believe Ubuntu already has the USB drivers installed.

---

### Post by eckeroo on 2009-01-18
> 
Well I believe Ubuntu already has the USB drivers installed. 

But will Ubuntu have the drivers to utilise the USB2.0 PCI card? Such devices come with Windows drivers, so it stands to reason that they will require Linux drivers.

Thank you for pointing out where I can get a Rosewill card, but shipping it from the USA would take too long and add unnecessary costs.

Regards

---

### Post by spoons on 2009-01-18
Don't know if this helps, but I put a USB 2.0 card in a Windows XP box the other day and it automatically detected the card and installed generic drivers which worked fine and there was no need to the use the drivers on the disc. I imagine Ubuntu would be the same.

---

### Post by eckeroo on 2009-01-18
> Don't know if this helps, but I put a USB 2.0 card in a Windows XP box the other day and it automatically detected the card and installed generic drivers which worked fine and there was no need to the use the drivers on the disc. I imagine Ubuntu would be the same.

I had a search through the Synaptic Package Manger and could not find any drivers, generic or otherwise, for USB PCI cards of any description. There are drivers for USB wireless and smartcard readers (devices that attach to the USB ports), but none for USB2.0 PCI controller cards.

---

### Post by eckeroo on 2009-01-20
I bought a PC LINE 5 port USB2.0 PCI card with Plug and Play, installed it into my computer, and it worked without any additional drivers and so on. I'm now getting 6 Mb/s download rate with my USB 2.0 sticks :)

I have not been able to provide a reference for the compatibility of Plug and Play devices for Ubuntu, but I can tell you that my new card is a VIA USB 2.0 Host Controller with the VT6202 chipset.

eckeroo

Hardy 8.04

---


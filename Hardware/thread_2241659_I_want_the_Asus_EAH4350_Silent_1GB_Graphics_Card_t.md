---
title: "I want the Asus EAH4350 Silent 1GB Graphics Card to work under ubuntu 14.04"
date: 2014-08-27
forum: Hardware
---

### Post by Martin Walters on 2014-08-27
I have an Asus EAH4350 Silent 1GB Graphics Card which has a Windows drivers cd.
I want the card to work under ubuntu 14.04.
any advice would be helpful.

thanks

---

### Post by ajgreeny on 2014-08-27
It looks as if that card is actually a Radeon HD 4350 graphic card (perhaps with a few tweaks from Asus) but at least that means it should work with Ubuntu using the open source radeon driver in 14.04.

You will not get the fglrx proprietary driver to work with that card in 14.04, but many users say the the radeon driver is now extremely good.  You will not have to install anything to get it to work as the radeon driver is installed by default in ubuntu, and will (or should) just work at boot.

---

### Post by Mark Phelps on 2014-08-28
>  which has a Windows drivers cd.

Sorry, that has only Windows drivers -- which will not work in Linux.

As ajgreeny pointed out, the default Radeon open-source drivers (which are automatically installed with Ubuntu) are the ones that will work with that card, now.

---


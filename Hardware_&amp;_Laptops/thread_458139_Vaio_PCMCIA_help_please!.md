---
title: "Vaio PCMCIA help please!"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by Radamand on 2007-05-29
Hi all, i am relatively new to Linux and have one small problem, I have Ubuntu feisty installed on my Sony Vaio PCG-GRT100 laptop and I can not get the system to recognize my PCMCIA card slot (oddly enough it used to work fine under dapper).  I have a Netgear PCMCIA wireless card that i'm trying to get working and it doesn't recognize it at all.

uname -a
Linux Radamands-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

im not sure what other info to provide, if you need more just ask.

---

### Post by rondackcpu on 2007-05-29
Welcome, Radamand,

First let's try to find which NetGear PCMCIA card you have.  Some of them are supported by the built in drivers of 7.04, some are not.  Please post as much info as you can about the card:  model number, version number, country of manufacture, etc.  It would help, too, if you opened a terminal (Applications>Accessories>Terminal) and typed the command "lspci" without the quotes.  The response will be a lot of the hardware connected to your machine.  Look for a line that says something about an Ethernet Controller.  It will give the name of the chip set in the card, and confirm that the card is properly seated in the slot.

CRS

---


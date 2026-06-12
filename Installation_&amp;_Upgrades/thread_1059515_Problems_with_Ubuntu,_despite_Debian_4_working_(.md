---
title: "Problems with Ubuntu, despite Debian 4 working :("
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by The Internal on 2009-02-03
Greetings,

I'm new to linux, but am an experienced computer tech (specializing in hardware troubleshooting and repairs for windows desktops).
I successfully (and easily) installed the most recent stable Debian build onto an old computer I recently acquired and after install, struggled to find working repositories
I'd really like to run Ubunutu after checking out a live session on another computer.
However, Ubuntu quickly starts a huge list of numbers and exceptions when I run the installer.
Before getting to the numbers and exceptions, it says something about my BIOS age failing the cutoff, saying it's from 1997 and the cutoff is 2000 or something like that. That struck me as odd. The BIOS is the latest release done by the board manufacturer, and is dated 2002.
There's also something about ACPI=force. From what I understand that has something to do with power management, though I don't understand why Debian didn't hiccup about the install, but Ubuntu is giving me the message.
After seeing a small bit of Ubuntu load bar, the screen starts listing row after row of "ata2.00: status {DRDY} <numbers>
ata 2.00: Exception Emask <more numbers>" with the numbered sequence on the far left rising each line.
I've not had this issue when I run a live session on any other computer.
I could really use help here. I've no idea why Ubuntu is doing this, especially considering that the same computer runs the latest stable Debian release without a hitch.
 
The motherboard is a PCCHIPS 817L rev. 1.0, with 256MB SDRAM, a new Athlon XP 2000+, a 120 GB WD IDE HD, an old 40 GB IDE hard drive of some kind, a 10/100/1000 NIC in a PCI slot, and PCI EVGA Nvidia 5200 graphics card.

---

### Post by The Internal on 2009-02-03
well, by adding "irqpoll ACPI=force" after hitting F6 at the install screen, I can at least get to the partitioner now. Hopefully I figured the problem out. Not sure what exactly irqpoll is doing (I'm assuming verifying the device IRQs?), but I saw it suggested for the DRDY error.

---


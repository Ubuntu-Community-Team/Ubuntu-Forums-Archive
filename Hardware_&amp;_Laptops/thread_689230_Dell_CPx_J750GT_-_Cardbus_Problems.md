---
title: "Dell CPx J750GT - Cardbus Problems"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by coeus1982 on 2008-02-06
Hi all,

I have an old Dell Latitude CPx J750GT, on which I have installed Xubuntu 7.10. The install went well and I have the desktop up now. Unfortunately, this laptop does not come with an in-built network card and I have a couple of different cardbus cards which I was hoping to use. One is wired and the other is wireless.

When I insert either card Xubuntu hangs. Or more accurately it "pauses", because when I remove the card it works again. What's more is that the time actually stops. If I run the date command before I insert the card, then insert the card, wait one minute and remove the card and run the date command again the time elapsed is a few seconds (which is the amount of time taken to insert/remove card). 

I have tried to boot with acpi=off to see if that makes any difference, I tried to perform a reinstall with the card inserted (same sort of behaviour, stalls until the card is removed), and I tried to boot Knoppix (to prove that it wasn't some quirk of Xubuntu.) I tried boot to recovery mode and inserted the card which gave the error "cardbus not supported", which probably makes sense.

I'm a bit stumped as to what to do to try to solve the problem, as I cannot run any commands when the card is inserted. I'm tempted to install Windows to try to prove that its not a problem with the bus or cards.

I have updated the BIOS on the laptop to A16.
The Laptop has an 750 MHz processor with 512 MBs Ram and a 20 GB harddisk.

The two cards in question are 
1. Xircom Cardbus Ethernet 10/100+Modem 56 (RBEM56G-100) (not supported as far as I can see)
2. Linksys WPC54G ver. 1.2

If anyone has any ideas I'd appreciate it.

---


---
title: "FYI: PCMCIA card in Dell Latitude CPi not working, HD corruption suspect"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by paulhurleyuk on 2007-11-17
I wanted to post this in case a) it happens to anyone else and b) anyone can explain why it happened !

I've got a Dell Latitude CPi PII 300Mhx laptop, that I'm in the process of turning into a digital photo frame.  I installed Xubuntu via a text install, and had everything working, including the 3Com Megahertz PCMCIA Lan card.  I then dismantled the laptop (carefully) and fitted it into a frame.

When I booted it up I couldn't get the LAN card to work.  I tried many things, including stripping the hardware and re-assembling it, installing PCMCIA-CS to no avail.  I also tried to install the Netgear Wireless PCMCIA card from my usual Compaq Armada M300 laptop.  This showed up in lspci, showing it was working, but ndiswrapper gave errors along the line of 

Failed to open config file /etc/modprobe.d/aliases

and several others.  I was trying several things when I noticed that the folder /etc/pcmcia was not showing up as a folder, and the permissions where ?????????.

I suspect the filesystems got corrupted in some way, which killed of pcmcia and other things.  I'm now re-installing xubuntu, and the lan card works during the install, so it was a software issue.

Hope this helps someone out there....

Paul

---

### Post by paulhurleyuk on 2007-12-26
Just a quick note to add that reinstalling the software worked a dream.  The PCMCIA card works now.

Thanks

Paul.

---


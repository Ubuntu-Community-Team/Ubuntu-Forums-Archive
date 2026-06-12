---
title: "HP Laser Printer prints only the first page"
date: 2020-12-09
forum: Hardware
---

### Post by agostino2 on 2020-12-09
Hello, It is quite an urgent problem because I work on it. I have already contacted HP support and they replied that they do not provide assistance on Linux systems. I bought an MFP 135a laser multifunction printer connected by USB port and when I send the prints it prints only one page, the first! If the document is, for example, is made of 5 pages, it prints only the first and subsequent rows of hieroglyphs. I got the drivers from the HP site, there is only one driver for Ubuntu. To print the 5 pages I have to turn the printer off and on once for each sheet! 5 reboots for a document, you understand that this cannot go on. But with Windows it works. I've been using Ubuntu 14.04 LTS extended support for years, so updated. And it works very well on everything, so far even with the old Samsung printer never caused trouble, but now the old lady is broken (the Samsung printer). If anyone can help me, I think it's a driver problem but HP didn't want to know about it, they said they release a single driver for linux systems and for any problems they don't assist customers who use different Windows systems and Mac. What should I do then? It could be the same for other manufacturers like Samsung or other brands if you buy a new one. Linux is open source so what do we do? Thank you all

---

### Post by slickymaster on 2020-12-09
Thread moved to **Hardware** for a better fit

---

### Post by Autodave on 2020-12-09
I have never had to install any driver for an HP printer.  And I have 5 of them going right now: 4 USB connected and one wireless.  You should not had to install any driver: just connect the printer and Linux does the rest.  There is probably a problem with the driver that you installed and there is most definitely a problem with you running 14.04 !  That reached its end of life (EOL) quite awhile ago and needs to be replaced now.

I would back up everything that I needed to keep, do a fresh install of 20.04 (with the printer turned on and connected to the PC) and go from there.  You most likely will not have to do anything else.  You could install hplip and hplip-gui after everything is up and running again.

---


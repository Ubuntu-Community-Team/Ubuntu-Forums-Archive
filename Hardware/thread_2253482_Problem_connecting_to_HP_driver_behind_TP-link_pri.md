---
title: "Problem connecting to HP driver behind TP-link print server"
date: 2014-11-20
forum: Hardware
---

### Post by YTS_Chan on 2014-11-20
Hi everyone. I am new to ubuntu. Previously tried to use linux during college for homework. Recently my hard disk die and I need to set up everything again after switching to my new hard disk. At the same time Microsoft  announced the new loophole where my previous XP will not be protected against.... so I decided to give Ubuntu a try. Until now, it is difficult to set up but I was able to set them up after some trials, except the printer which is shared among my family with a print server.

First of all, some basic information:
Ubuntu version: 14.04.1 LTS
Printer: [HP LaserJet Pro M1132 MFP]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&product=3965851")
Print server: [TP-link TL-PS310U]("http://www.tp-link.com/en/products/details/?categoryid=232&model=TL-PS310U")

I have already installed the driver for the print server following this guide:
[http://www.tp-link.com/en/article/?id=352](http://www.tp-link.com/en/article/?id=352)

And I have already installed the printer driver using hplip. I can already print the test page if the printer is directly connected to my computer. The problem is that I failed to print if the printer is behind the print server.

On CUPS I was able to find printer on and choose the driver I have downloaded wit hplip and add the printer to the printer list. However, when I tried to print the test page, there is no response.

Any clue on what is the problem?

---

### Post by Mark Phelps on 2014-11-20
> And I have already installed the printer driver using hplip. 

I think THAT was a mistake.

The guide you linked showed HOW to add a printer and the proper driver and, it does NOT appear to use HPLIP.

I've done stuff like this myself with other print servers, and it was important to do EXACTLY what the guide said, otherwise, the print server would not work.

---

### Post by celsoale on 2015-08-30
I had the same problem and solved using the HP Laser Jet M1120 MFP Footmagic driver (i think it comes with ubuntu, don't use the hplip), with AppSocket/HP Jet Direct. I read that the hplip doesn't work with print server, so you have to use the footmagic. But on footmagic site, I didn't find the M1132, so I tryed this and worked fine.

---


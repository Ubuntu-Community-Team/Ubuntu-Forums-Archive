---
title: "cartridge not recognized after installing scanner driver for Epson SX515W"
date: 2010-03-17
forum: Hardware
---

### Post by surfeuse on 2010-03-17
hello,

I have a new Epson SX 515W that works fine on wnidows XP. 
I now want to make it work on ubuntu 9.10. The printer was recognized automatically (althought the driver chosen is SX 405), and I have downloaded the driver for the scanner in avasys web site. I choose the deb file and installed it successfully. 
Since then, I have an error message on the screen of the printer : "cartridge not recognized" and I can't use it anymore !! Even on windows, it does not work anymore. I have to precise that the printer is new, so are the cartridges. And anyway, I don't understand why the scanner does not work anymore, since it does not need cartridge to scan !
Please, help me : I'm a rooky ;) 
thanks a lot in advance
&#12288;

---

### Post by ajgreeny on 2010-03-17
Try to remove and then reset the cartridge, after very gently cleaning the copper contacts on it, and also in the cartridge bay, if you can get to them.  It may simply be that it is not seated properly, though I am surprised it works in Windows if that is the problem.

---

### Post by surfeuse on 2010-03-17
thanks for your answer ;)
well, I'll try that tonight, but I doubt it will solve my problem, because it was working perfectly until I install the driver. So I was more thinking about a software problem.
I have been able to print from ubuntu before installing that driver for the scanner. Is that possible that installing a driver on my computer has affected the printer's soft ? I hope not... 

Just to clarify the situation : before, the printer and scanner were working with windows, the printer was working with ubuntu and I was able to use it without computer to copy documents. Then I installed the driver for the scanner on ubuntu and now, nothing works anymore !! I'm in despair. I'm trying to convince my partner to use ubuntu instead of windows, but if it breaks a new multifunctions printer, I'm not sure I'll convince anyone ;)

An other question : the driver I'm using for the printer is the one suggested by ubuntu and is for SX405 while I have a SX515W. The driver I'm using for the scanner has been downloaded from the avasys web site and is dedicated to SX515W (and a few other printers). Could it be that there is an unconsistency between these 2 drivers ? but if it is the case, why does it affects the printer also in standalone mode (for copy) or with windows ?

---

### Post by ajgreeny on 2010-03-17
OK, I see what you mean.  I suspect the problem is related to the two different drivers for the one machine conflicting in some way.

Is it possible to use the same version of driver for the printer part of the machine that you use at present for the scanner, thus avoiding any conflicts between them.  It's a while since I used an Epson machine and then it was a printer only, so I'm a bit out of touch with their machines these days.

---

### Post by stanleyndeg on 2010-08-16
Same problem with Ubuntu Lucid 10.04; SOLVED.
SX515W worked fine with the drivers from the avasys website on a 10.04 upgrade from 9.10.  On two computers with a 10.04 clean install attempting to scan using Xsane crashed the printer requiring printer restart and the removal and replacement of the ink cartridges to get them recognised. 
The version of sane (read from Xsane->File->Info) was 1.0.21 on the upgraded and working machine and 1.0.2 on the clean installs.

The working machine (the upgrade) had this extra line in /etc/apt/sources.list

[FONT="Courier New"]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe[/FONT]

With this line added to the clean install machines then doing update and safe-upgrade my printer/scanner is fully functional on all three machines.

Hope this helps. 

The SX515W seems to be an OK device. 
Pity there's no setup application for Linux as setting up by hand from the printer's panel is very tedious. It might be worth borrowing a windows computer just to set up the printer --- giving it back quickly afterwards of course

---


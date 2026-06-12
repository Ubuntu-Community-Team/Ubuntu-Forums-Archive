---
title: "Printer prints PDF only on Ubuntu 13.04"
date: 2013-10-25
forum: Hardware
---

### Post by Kaminar on 2013-10-25
Hi,

I discovered problem with printing under Ubuntu 13.04. The printer prints PDF documents only. If I print via LibreOffice or text editor (bundled with Ubuntu) the printer prints blank pages only. In some cases it prints only frames from LibreOffice Calc without any texts.

The printer is HP LaserJet Pro 400 MFP M425dn which is connected via Ethernet. On previously installed version of Ubuntu 10.04 this printer was printing without any problems.

The similar problem I noticed with older HP DeskJet 840C (connected via USB) which prints distorted and unreadable text even if it is printed form PDF. On previously installed Ubuntu 10.04 there were no problems.


Have you any clue where is the problem?

Regards
Kaminar

---

### Post by Jonor on 2013-10-25
My HP printer recently produced distorted printout so i opened the HPLIP toolbox in Ubuntu 13.04 Apps and clicked the hammer button to Diagnose The HPLIP Driver which apparently was not up to date.
After following that i did a first level clean since the printer had not been used for a while and it worked properly from then on.

---

### Post by Kaminar on 2013-10-26
Before I do anything with the printing in Ubuntu I did updating of Ubuntu. After it I again try to print something and surprisingly both printers work fine now.

I guess something wrong happened during any updating in the past and todays update corrects the printing.

Anyway, thank you for the advise

---


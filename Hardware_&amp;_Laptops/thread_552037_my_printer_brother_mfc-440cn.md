---
title: "my printer brother mfc-440cn"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by pierre in USA on 2007-09-16
:confused: I am a novice ubuntu user. More so, I have just recently migrated  from XP to the linux world. I am unable to find a driver for my new printer brother mfc-440cn. Well, I already went on brother web site, however, I was easily lost and over my head in knowledge.  I have been trying to find a solution for the past week. So far, I ha  d no success.


I understand the world of Microsoft has sheltered me from real computing. However, I am very eager to learn and familiarize with ubuntu /linux world.

Please, I would greatly appreciate anyone who would cast any idea how I should go about solving my printing issue.

Thank you.... Pierre Drouin

---

### Post by linuxwizard on 2007-09-16
[http://ubuntuforums.org/showthread.php?t=518448&highlight=brother+mfc-440cn](http://ubuntuforums.org/showthread.php?t=518448&highlight=brother+mfc-440cn)

Drivers for Debian look down list for your model
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

Howto install
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)

---

### Post by asforme on 2007-10-06
I'm not sure I understand this.  I downloaded the driver, installed it.  According to the site:

> This will install the Brother printer driver onto your computer and configure it to use the USB interface.

If you are using a USB interface, you do not need to make any further modifications and you can print from your Linux application.

However, no new printer has shown up, and when I add a new printer and select a driver, under the Brother make there is still no MFC 440CN.  As far as I can tell installing that deb package did nothing.  Can someone help me out?

---

### Post by larytet on 2007-11-15
worked for me MFC-440CN, Ubuntu 7.04 - the Feisty Fawn - released in April 2007.
I am using USB, i checked only printing so far, i did not try scan and fax

Important note first. I had "sane" package installed well before. I needed sane for Epson CX3900. To install sane I downloaded a driver from [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) and install the RPM using "alien". Now, I do NOT think, that you need to install driver for CX3900 before you can use Brother, but i have little doubt, that you need "sane" at least for the scanner.

Page "Installing and using a Brother printer driver into a Linux based system using the LPD service (lpr)"
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)

I just run deb directly from the WEB site, but i guess something like
sudo dpkg -i  mfc440cnlpr-1.0.0-9.i386.deb 
will do

after that cups driver (wrapper ?) from page "Brother CUPS driver and CUPS Wrapper driver download"
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

sudo dpkg -i mfc440cncupswrapper-1.0.0-10.i386.deb

After that menu System->Administration->Printing
Right mouse click, Add printer in the window

You will see (at last I seen) that MFC440CN connected to USB1 (or something like this). click forward.
On the list of the printers there should be the exact printer MFC 440CN. If it is not there you probably should check the driver again.

---

### Post by larytet on 2007-11-15
P.S. another important note 

On the brother WEB site they suggest to use --force flag in the dpkg of the driver. I did NOT use --force flag for the cup wrapper and for the driver. I prefer to see the errors and try to fix it, but there was no any errors. 

The dpkg command in my previous post  did the trick for the cups wrapper
gdebi-gtk installed mfc440cnlpr for me

---

### Post by dburnett77 on 2008-01-09
These days, w/ 631 so readily avail. in the CUPS arena, I'd recommend going to a 32-bit OS vers. of Ubuntu.  Painful, maybe, but Flash will work better.

If you have to have 64-bit, Brother's website has the directions for that, also.

But, as I stated, 32-bit is much more stable.  As, it allows the processor capable of 64-bit operations about 1/3 overhead.  Heck, I've got to rastle to maintain an open connection, and still some manage to grab the job if I'm connected.

---

### Post by IncomingFire on 2008-03-05
... 1 year old bump, but I've followed everything but am not able to print via network.  Everything is recognized by my printer just shows receiving data forever and never prints a thing.

Any help that could be provided would be appreciated.  Thanks.

---

### Post by linuxwizard on 2008-03-05
Look over these
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by IncomingFire on 2008-03-06
...that is good info wiz, but the 440cn comes with a print server built in, what I'm talking about is I'm actually running cat-5 from my router to my printer not sharing the printer via another computer on the network.  I'm sorry I did not explain the more clearly in my first post.

---

### Post by ardoaamch on 2008-03-07
I did a write up on this printer on my site:

[http://adammichaelroach.com/2008/03/03/how-to-brother-mfc-440cn-on-ubuntu-linux-710-gutsy-gibbon/](http://adammichaelroach.com/2008/03/03/how-to-brother-mfc-440cn-on-ubuntu-linux-710-gutsy-gibbon/)

---

### Post by luvit on 2008-03-14
Hi. I installed my Brother MFC-845CW today and it seems to work well on my clean install of v7.10.  I outlined all the steps I took to install it in my blog (see my signature).

My experience is for the MFC-845CW, but I wrote the outline and provided links to Brother's files in hopes it would benefit other models.

Please let me know if the outline is easy to follow. --Thanks! ...and good luck.

---


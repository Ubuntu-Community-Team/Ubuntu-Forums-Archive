---
title: "hp deskjet 3550"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by bandito40 on 2008-02-07
Hi,

I was wondering if anyone here has been able to get one of the HP DeskJet series printers working with Ubuntu.  I have tried variuos installations of HPIJS and HPLIP drivers but my printer (Hp Deskjet 3550) will just not print. The jets go back and forth but no ink comes out and I have just put in a fresh cartridge. 

I have tried installing via CUPS, also auto install and manual install directly from the driver itself.

The printer was working on windows before I got it. Anyone have any thoughts one this?

Thanks,


Carl



[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by linuxwizard on 2008-02-07
Have you tried using the HP Toolbox/HP Device Manager ? Setup printer there the toolbox has maintenance features, cartridge alignment, check ink levels. Also more printer settings you can adjust.

---

### Post by bandito40 on 2008-02-07
Well, I downloaded the HP utilities.  At first only hp-clean would work but I still couldn't print anything.  I deleted all other printers and re installed the driver with hp-setup.  This corrected two things.  One it gave me the correct uri that I could copy for the cups web page and finally allowed me to align the printer.  I ran hp-clean a few more times but other then printing the alignment page, I have not been able to print anything.  Any other things I could try?


Thanks,


Carl





[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by holmestp on 2008-02-08
I have the same problem with an HP Officejet 6310 and an HP Business inkJet 1100, have an HP Laser that works fine, so seems to be an inkjet problem.  My 6310 worked great with version 7.04, but will not print in 7.10.  Its recognized, I can make copies with the 6310 but Ubuntu will not let it print.

You might add your post to the Incompatible hardward list, under the Hardware compatibility list.  There should be a category just for printer problems.
[http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236)

---

### Post by bandito40 on 2008-02-09
Funny, after reading a few of the posts on that thread it seams pretty straight forward to setup a hp printer, especially on 7.04 which I am using.  Is there some configuring I have to do in the X11 configuration file or run some usb utility besides lsusb?

Thanks


Carl



[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by linuxwizard on 2008-02-09
bandito40
No you don't have to configure X11. Most HP printers plug them in they are auto detected now all you have to do is set them up. You do not need to install HPLIP already installed you don't need to remove anything. And no you don't need the newer version of HPLIP just because it is available. Myself I have 3 HPs Deskjet, PhotoSmart, Laserjet I can have all 3 installed setup the way I want them in less than 10 minutes. Lets see if M$ can do that. All 3 works better and faster and they ever did on M$. Same computer. I use Dapper, Feisty, & Gusty both Ubuntu/Kubuntu all 3 works the same in all systems. One of the biggest problems I see is alot of people think they have to install drivers when they add new hardware but in some cases things will just work without doing anything. It is when you start adding and removing/reinstalling drivers where the issues are when you don't need to. IMO

---

### Post by bandito40 on 2008-02-10
Ya,  it started out that way which is the way I start out with all hardware. I plugged it in and nothing happen.  Then tried adding a printer which needed the driver and then trying what I guess to be every combination of adding a printer via hplip but still no luck.  Maybe there something in the setup of the printer as you said that I missed.  How did you setup your printer??


Thanks,

Carl


[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by linuxwizard on 2008-02-10
Here is your printer > [http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3550](http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3550)


When you went and tried to add your printer >System > Administration > Printing  > New Printer > Your printer should have been detected > HP DeskJet 3550 > you want to take Recommend/Suggested driver > keep going forward

This would be for all printer not just HP
[https://help.ubuntu.com/7.10/printing/C/printing.html#local](https://help.ubuntu.com/7.10/printing/C/printing.html#local)

This guide show Dapper but it gives a general idea
[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

Than you need to add the printer in HP Toolbox/HP Device Manager

---

### Post by bandito40 on 2008-02-11
I could rip hair out!!!

Thanks,  that worked perfectly.  Maybe my printer was working the entire time.  I never actually tried to print something other than the test page from the regular printer settings. I also wasn't aware how to access the hp-toolbox until I read the tutorial.


Thank you very much,


Carl



[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by linuxwizard on 2008-02-11
You're Welcome, Glad to hear you now have your printer working. Please mark thread as SOLVED.    [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


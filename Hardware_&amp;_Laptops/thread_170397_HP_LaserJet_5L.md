---
title: "HP LaserJet 5L"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by skippy81 on 2006-05-04
Greetings all! :D 

Ok now its time to whinge....

I am trying to install a printer, it is a HP laserjet 5L - tested and working with windows (and im pretty sure I had it working on a slackware box a couple of years ago).  It connects using a parallel cable only unfortunately.

I have tried the built in gnome CUPS utility (system-admin-printing).  Sometimes the proggy locks up, and when run from a terminal I get loads of warnings come up such as:> WARNING **: Two ppds have driver == 'hpijs (recommended)'

I have managed to setup the printer with the Gnome utility in the end, but when I attempt to print anything I just get junk pages with a line or two of random characters.  These junk pages continue until I cancel printjob AND turn off printer and computer.  Its driving me mad!! :p  I have tried all the suggested drivers through the GUI, including the ljet4 one, which is said to work perfectly here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_5L]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_5L")

I want to try and use the cups web interface to have a crack at installing the printer, but it's nannying me > Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing..  I have tried editing  /etc/cups/cupsd.conf and changing "RunAsUser Yes" to  "RunAsUser No" but still the evil web interface won't let me in. 

Does anyone please have any suggestions, whether they are specific or general, as to how I can:
a) use the webinterface
b) make my printer work

thanks guys

---

### Post by skippy81 on 2006-05-04
Fixed!!! :D 

**Changed parallel port mode from "ECP" to "Normal" in my BIOS settings**.  I suggest anyone using parallel connection and recieving junk pages checks this out.   

Also I found that if you want to use the CUPS web service you can assign a password to root with "sudo root passwd" in order to get in to the web interface (you will probably also have to change the "RunAsUser Yes" to "RunAsUser No" in /etc/cups/cupsd.conf).  Note that being able to access CUPS web service was not the thing that fixed my problem, it was all in the BIOS.  

I still don't know why the gnome utility was locking up, but I'm beyond caring now, my PC is fully functional!!! :razz: 

All in all I have found my expierience of Ubuntu pretty good.  The biggest flaw I have found in the installation has actually been the fact that my sis190 lan card was not supported.  I had to download GCC 3.4 to an other PC, install the kernel sources from the CD and mess about for over an hour on a makefile which required a tab character to make it work :p Other than that, this has been my smoothest expierience of linux yet - if the network card driver had been included then I would say that Ubunto is 100% noob friendly ;)

---


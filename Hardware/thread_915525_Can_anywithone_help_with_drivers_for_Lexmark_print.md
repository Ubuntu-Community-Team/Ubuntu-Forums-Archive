---
title: "Can anywithone help with drivers for Lexmark printer"
date: 2008-09-09
forum: Hardware
---

### Post by ZALinuxDude on 2008-09-09
Hi guys I need help trying to find drivers that will allow me to print using my Lexmark x2650 printer from my Xubuntu Hardy setup Ive tried google but don find anything concrete any help will be appreciated... thanks

---

### Post by wenuswilson on 2008-09-09
[http://ubuntuforums.org/showthread.php?t=519990](http://ubuntuforums.org/showthread.php?t=519990)

Give post #4 a shot.

[http://downloads.lexmark.com/perl/downloads/downloads.cgi?ccs=229:1:0:390:0:0](http://downloads.lexmark.com/perl/downloads/downloads.cgi?ccs=229:1:0:390:0:0)

...Link to the driver, use the red hat linux one.

I don't have that type of printer so I can't help anymore then that.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X2650](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X2650)

...Link stating that that printer only works "partially".

---

### Post by phyz on 2008-09-10
i'm also using lexmark x2650 with Ubuntu Hardy.i've tried to use the z600 driver but it does not work at all...

---

### Post by Sef on 2008-09-10
[Open Printing]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X2650") says it works partially.  If you want it to work fully, then set it up on a windows print server.

---

### Post by ZALinuxDude on 2008-09-12
Do you think if i used Wine and then just loaded the windows software via Wine, it'll work?

---

### Post by Sef on 2008-09-14
> Do you think if i used Wine and then just loaded the windows software via Wine, it'll work?
Doubtful, but check [WINE]("http://winehq.org") for a definite answer.  WINE is for applications.   A print server is easy to set up.

---

### Post by Magic_Spehar on 2008-11-24
[http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)

Here you will find a driver for Ubuntu 8.04 (it also works for Ubuntu 8.10, I tried it myself) for the Lexmark x2650.

---

### Post by captain_sensible on 2008-12-17
hi,

im using ubunto 8.10 ,& have a lexmark x2650  i followed the link suggested by Magic_Speha downloaded the file lexmark-inkjet-08-driver-1.01.i386.deb.sh ran it & it works fine.

funny thing I emailed lexmark only two weeks ago & they replied saying 
lexmark doesn't work with linux ?

anyway i'm now  happy man!

cheers

---

### Post by afrodeity on 2009-03-27
Looking for the 64bit version of the above driver. I've been told one can also download 32bit libraries using[ Getlib?]("http://ubuntuforums.org/showthread.php?t=474790")
Does anyone have a link?

---

### Post by mister_playboy on 2009-03-27
Do you have enough RAM to spare for a Win 2000 or XP virtual machine?  That was my only choice to use my Kodak printer, but it works perfectly!  Just install the Windows drivers (from the included CD, in my case) to the virtual machine.

Takes a bit of learning to set up, but well worth it.

---

### Post by afrodeity on 2009-03-28
I now have virtualbox running with XP, and it does seem to run faster in emulatin than natively. Tried setting up the Lexmark pack/drivers, but the software can't find my network. Gave me two options, usb or connected to another computer. Both don't work. I've now tried this hack: [http://seogadget.co.uk/enable-usb-support-virtualbox/](http://seogadget.co.uk/enable-usb-support-virtualbox/) and will see what happens when I log out and back. :)

---

### Post by afrodeity on 2009-04-07
I set up the XP in Virtualbox, and yes, I can boot it up whenever I need to do serious printing, but how do I set up a network printer to the Virtualbox, so that I can print within ubuntu and spool out in windows?

Of course, the real driver would be great. There's a X86 driver, and 64bit for Windows, but no 64 bit deb for Ubuntu. Surely Lexmark realise there are a lot of ubuntu users with Lexmark issues in South Africa and around the world?

---

### Post by jbdavis52 on 2009-04-25
> **Magic_Spehar said:**
> [http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)

Here you will find a driver for Ubuntu 8.04 (it also works for Ubuntu 8.10, I tried it myself) for the Lexmark x2650.

That link is dead. It will lead you to the company's home page (US version). You can go through the menus for nation and language, etc or just use [http://www.lexmark.com/](http://www.lexmark.com/) then use the drivers and downloads menu. Pick the driver finder and on that page use the select printer type menu and choose the consumer inkjets and then on that screen, find the icon for the z2300 and click on download driver. There you will find the OS menu and when you click on Linux, you will find the various flavors. This is where the  lexmark-inkjet-08 zip files will be found. There is also a 3rd party ftp site, but I can't find the link to it right now.

Hope this clears the mud a little.

John

---

### Post by afrodeity on 2009-05-11
Still no 64bit drive and the  32bit can't install with getlibs because its a script.

---

### Post by afrodeity on 2011-06-13
The dreaded problem comes returns with Ubuntu 11.04

---


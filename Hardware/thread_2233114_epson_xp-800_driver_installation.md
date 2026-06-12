---
title: "epson xp-800 driver installation"
date: 2014-07-06
forum: Hardware
---

### Post by jgw on 2014-07-06
I have an epson xp-800 all in one inkjet.  I went to system printers and added that printer (it found the printer just fine).  Then it wants to install the driver.  I choose the driver epson-inkjet-printer-201208w   I also understand that I will also have to find a driver for the scanner but, first, I just want to get the printer installed.  Its says its installing but it says that for 2 hours and the installation isn't even half installed.    The current installation try, which has been running for 20 minutes, doesn't even show the beginning of the progress line.

Anybody have any thoughts on this one?  

Thank you.......................

---

### Post by Mark Phelps on 2014-07-06
There are problems installing Epson drivers -- discovered this when I recently installed Ubuntu 14.04 and tried to add my Epson printer.

The problem, so others have claimed, is that the Epson driver expects a package (lsb) to already be installed and hangs if that is not the case.

You can try installing the package lsb from Synaptic Package Manager -- and see if that works.

What worked for me was using CUPS to install the Epson printer.

---

### Post by jgw on 2014-07-06
Thanks for the reply - I will give it a shot.  thanks again!

---

### Post by sammiev on 2014-07-06
I never had much problems with Epson printers or scanners. 

I use this [Epson]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") site for my drivers. 

Type in "xp-800" in "Enter product name".

---

### Post by pdc on 2014-07-07
absolutely

go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18782&DSCCHK=1656158aae493417d004b0d5801c13d672b30c9a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18782&DSCCHK=1656158aae493417d004b0d5801c13d672b30c9a)

[COLOR="#008000"]epson-inkjet-printer-201208w_1.0.0-1lsb3.2_i386.deb[/COLOR] or [COLOR="#008000"]epson-inkjet-printer-201208w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

---

### Post by jgw on 2014-07-07
Thanks for the replies!

I made a run at installation and got:
greg@greg-MS-7222:~/Downloads$ sudo dpkg -i epson-inkjet-printer-201208w_1.0.0-1lsb3.2_i386.deb
Selecting previously unselected package epson-inkjet-printer-201208w.
(Reading database ... 389727 files and directories currently installed.)
Preparing to unpack epson-inkjet-printer-201208w_1.0.0-1lsb3.2_i386.deb ...
Unpacking epson-inkjet-printer-201208w (1.0.0-1lsb3.2) ...
dpkg: dependency problems prevent configuration of epson-inkjet-printer-201208w:
 epson-inkjet-printer-201208w depends on lsb (>= 3.2); however:
  Package lsb is not configured yet.

dpkg: error processing package epson-inkjet-printer-201208w (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 epson-inkjet-printer-201208w

I then went back to synaptic to check on my lsb installation.  One thing did not show installed: liblinux-distribution-perl.  I checked it for installation and got:
E: libpam-systemd: 7.89474:subprocess installed post-installation script returned error exit status 1
E: man-db: subprocess installed post-installation script returned error exit status 1
E: lsb-core: dependency problems - leaving unconfigured
E: lsb-graphics: dependency problems - leaving unconfigured
E: lsb-cxx: dependency problems - leaving unconfigured
E: lsb-multimedia: dependency problems - leaving unconfigured
E: lsb-desktop: dependency problems - leaving unconfigured
E: lsb-printing: dependency problems - leaving unconfigured
E: lsb-languages: dependency problems - leaving unconfigured
E: lsb: dependency problems - leaving unconfigured
E: epson-inkjet-printer-201208w: dependency problems - leaving unconfigured

I think I should probably uninstall lsb entirely and then reinstall.

I then thought it might be a good idea to reboot.  When I did that I got:
 package linux-image-3.13.0-30-generic 3.13.0-30.54 failed to install/upgrade: subprocess new pre-installation script returned error exit status 1

    Ubuntu
    &#8220;linux&#8221; package
    Bugs
    Bug #1338416

This being the case I suspect I am doomed until stuff gets fixed (perhaps its not ALL my fault? <G>)



Any thoughts on my mess?

---

### Post by jgw on 2014-07-07
OK, I got it running!  I had several problems.  I think the main one was: package linux-image-3.13.0-30-generic 3.13.0-30.54 failed to install/upgrade    To overcome that one I re-booted, reset my sources and ran program update.  This time it took, installed the image file, etc.  Then I rebooted again, and tried to install the driver again and, this time, it took!  Then I just went to my system setup/printers, added the printer, it found everything and I am now up and running with the printer.  I also noticed that there were other drivers for the scanner and fax modules in the printer.   I tried to install the scanner driver but failed.  I got:
greg@greg-MS-7222:~/Downloads$ sudo dpkg -i iscan_2.29.3-1~usb0.1.ltdl7_i386.deb[sudo] password for greg: 
(Reading database ... 389836 files and directories currently installed.)
Preparing to unpack iscan_2.29.3-1~usb0.1.ltdl7_i386.deb ...
Unpacking iscan (2.29.3-1~usb0.1.ltdl7) over (2.29.3-1~usb0.1.ltdl3) ...
dpkg: dependency problems prevent configuration of iscan:
 iscan depends on iscan-data; however:
  Package iscan-data is not installed.

dpkg: error processing package iscan (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 iscan

This one is odd.   I think this is telling me that it needs iscan-data and its not installed.  Its not installed because its part of what I am trying to install.  Then I went to synaptic to see what it had to say and it advised me that I had a broken program.  I then went to edit/fix broken package and ran that.  It said the dependency problem was fixed.  I then did a search (in synaptic) for iscan.  It found it, it was red with a big red x in front of it so I removed the entire thing.  I did that two times just to make sure.  So, now, I have a new problem.  This time installing the driver for the printer driver.

Any help on this one?

Thanks.......................

---

### Post by pdc on 2014-07-08
>  So, now, I have a new problem.

.............could you be more specific?

---

### Post by jgw on 2014-07-08
I couldn't install the scanner due to the errors noted in my last post.  I then found out that vuescan can run on linux.  ([www.hamrick.com](www.hamrick.com))  That being the case I went there and found Sane Epson Backend ([http://www.freecolormanagement.com/sane/libusb.html](http://www.freecolormanagement.com/sane/libusb.html)).  In theory this will allow me to do the sane thing, then install vuescan and I should be done.  I have owned vuescan for about 14 years and it is, in my opinion, a really good solution to scanning.  I have, however, not attacked this one yet but will soon and I will post the results here.

I simply downloaded the install file, clicked on it and the archive manager took care of everything and I suddenly had a vuescan folder.  I went there and double clicked on the vuescan program and it could not find the scanner.  Shut down vuescan.  I then went the the vuescan folder, bright up a terminal and entered "sudo vuescan.exe"  Vuescan could see the scanner (in my epson ex-800.  Tested the scanner and I am in business!

My next problem will be to figure out why I have to sudo the program to get it to run properly.  I think I will post that in a separate posting.  I will also mark this thread as solved.

---


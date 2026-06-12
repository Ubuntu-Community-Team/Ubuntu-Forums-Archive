---
title: "Canon Pixma MG4120 hooked up and recognised, drivers installed ... and still nothing"
date: 2013-06-17
forum: Hardware
---

### Post by hockeytux on 2013-06-17
Little problem here with my Canon Pixma MG4120 printer. Its hooked up to the PC (running Ubuntu 12.04), installed the drivers from the Canon website its recognised as a printer and visible in e.g Libre Office ... but it doesnt print. 

In Libre Office for example I get a 'Printing cancelled' message pop-up when clicking 'Print'. In GIMP I get no message at all.

Incidentally, when I put files on a SD card and insert it into the printer directly, it would recognise all jpgs on it but no docs or pdfs.

Is this something that can be fixed via PC or is this likely a printer issue. If so, can I or do I have to install new printer firmware via PC?

Thanks in advance.

---

### Post by ahallubuntu on 2013-06-17
~

---

### Post by hockeytux on 2013-06-18
I got mine from Canon's East Asia support website based on commonts I've seen in another post where someone found a good driver there. The packages I installed were in a driver bundle called cnijfilter-mg4100series-3.60-1-deb.tar.gz.

Not sure if that's the one I actually need. This was the only Debian driver I was able to find.

Also tried printing a test page from the 'system-config-printer' debugger. No success.

EDIT: Also just checked the Canon Europe website which you mentioned. The drivers are the same as on the Asian site: [                          MG4100 series IJ Printer Driver Ver. 3.60 for Linux (debian Packagearchive)]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG4140.aspx?DLtcmuri=tcm:13-875795&page=4&type=download") and [MG4100 series ScanGear MP Ver. 1.80 for Linux (debian Packagearchive)]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG4140.aspx?DLtcmuri=tcm:13-875799&page=3&type=download") for the scanner. Had to find them for the MG4140 though, my MG4120 was not on the list. The drivers seem to be for the whole 4100 series anyway however.

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by pdc on 2013-06-19
you are getting some very good advice from ahallubuntu

if you copy and paste 

> [COLOR="#FF0000"]sudo dpkg -l | grep cnijfilter[/COLOR]

into a terminal, it will show if the drivers were installed; 

eg for my MG3100 series I get

> [COLOR="#800080"]ii  cnijfilter-common  3.60-1 IJ Printer Driver for Linux.
             ii  cnijfilter-mg3100series 3.60-1 IJ Printer Driver for Linux.[/COLOR]


(and my MG3100 works finel.........)

---

### Post by hockeytux on 2013-06-23
I installed the driver via GDebi after downloading the .deb file.

After checking with sudo dpkg -l | grep cnijfilter, it looks like it installed properly:

> ii  cnijfilter-common                                           3.80-1                                     IJ Printer Driver for Linux.
ii  cnijfilter-mg4100series                                     3.60-1                                     IJ Printer Driver for Linux.
ii  cnijfilter-mg4200series                                     3.80-1                                     IJ Printer Driver for Linux.

I tried the MG4200 driver later as well, no luck obviously.

---

### Post by pdc on 2013-06-23
I would go the printers section in administration and delete all that you have there ........it ain't working................................

you have an MG4100 series printer...............so the goal ideally would be to go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100395002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100395002.html)

and download the [COLOR="#008000"]cnijfilter-mg4100series-3.60-1-deb.tar.gz[/COLOR]

to install it, the commands would be

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg4100series-3.60-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg4100series-3.60-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

.......and that should install the MG4100 drivers and you should have a working system

---

### Post by hockeytux on 2013-06-24
Cleared all existing drivers via Synaptic, got the one you mentioned from the Canon website above, untarred it via terminal and then when attempting to install it ([COLOR=#FF0000]sudo ./install.sh[/COLOR]) I got:

> ==================================================

Canon Inkjet Printer Driver
Version 3.60
Copyright CANON INC. 2001-2011
All Rights Reserved.

==================================================
An error occurred. The package management system cannot be identified.

What am I missing?

---

### Post by pdc on 2013-06-24
OK:

you don't tell us if you have 32bit or 64bit; but get it clear for yourself

if you open the [COLOR="#008000"]cnijfilter-mg4100series-3.60-1-deb[/COLOR] directory from the Downloads directory.........using the mouse..........ie click

................then open the directory [COLOR="#008000"]packages[/COLOR]........then you should see 4 packages: 2 for 32bit and 2 for 64bit;

you need to install the [COLOR="#EE82EE"]COMMON[/COLOR] package first and then the [COLOR="#EE82EE"]MG4100[/COLOR] package next; for the correct 32 or 64

right-click on the COMMON package first; select "[COLOR="#0000FF"]Install with Ubuntu Software Center[/COLOR]" and then repeat for the MG4100

..........that is what the install script would do ......................... it must find some rpm package in your system somewhere and baulk on that ..................

---

### Post by hockeytux on 2013-06-24
I did all that before starting this thread, with the exception that I used GDebi instead of Ubuntu Software Centre after right-clicking first the common and then the MG4100 packages to install them (i386 since I've got a 32-bit system). As that didn't work - I asked for help :)

I've now installed those with the Software Centre... same error. No response when attempting to print the test page and obviously no luck when attempting to print a doc in Libre Office for example.

Incidentally I noticed something else, not sure if that's got anything to do with my problem:
When I select Applications > System Tools > Printers, I get the following error message:
> Could not launch 'Printers'
Failed to execute child process "su-to-root" (No such file or directory)

When going to System Tools > System Settings > Printers however, I can see my printer ready to go. On the printer 'Options' page, I have added my username to the 'Allowed Users' list. That's the only user on this PC. 

Am I missing any dependencies?


Thanks in advance.

---

### Post by pdc on 2013-06-24
so you are using a stock,standard Ubuntu 32bit install?

> Failed to execute child process "su-to-root"

let me google that for you;

[http://ubuntuforums.org/showthread.php?t=969568](http://ubuntuforums.org/showthread.php?t=969568)

have a read at some of the posts in the above thread

you might choose the solution in post #16 sudo apt-get install menu

what does 

> sudo dpkg -l | grep cnijfilter

now yield?

---

### Post by hockeytux on 2013-06-24
Yes, standard 32-bit Ubuntu 12.04.

sudo dpkg -l | grep cnijfilter now gets me:

> ii  cnijfilter-common                                           3.60-1                                     IJ Printer Driver for Linux.
ii  cnijfilter-mg4100series                                     3.60-1                                     IJ Printer Driver for Linux.
rc  cnijfilter-mg4200series                                     3.80-1                                     IJ Printer Driver for Linux.


 EDIT: Also installed the menu and selecting 'Printers' no longer gives me an error message but prompts me for the foomatic-gui password - though that never launches. Nothing happens after I've entered my password there...

---


---
title: "Samsung scx 4200 ubuntu 8.04"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by andresmc on 2009-03-22
Hello everybody. Im new in Ubuntu, Im 5 weeks searching how to install my printer. Is a Samsung SCX 4200. 

Is a multifuntion printer and I want that the printer and scanner work correctly so, please help me with all the steps I have to do...

Thank a lot

---

### Post by yahs on 2009-03-23
Go to Samsung.co.uk
Download the driver (search for scx-4200)
the driver is the Samsung Unified Driver (ver 3.00.37)
Extract the file to Desktop. It will create a folder called cdroot
Open a terminal (Accessories-Terminal)
Change directory to /cdroot/Linux
Run this command - sudo ./install.sh (the full stop and forward slash are needed). Enter your password.
Follow the prompts, reboot and that's it.

---

### Post by andresmc on 2009-03-24
Hey friend thanks a lot, I did exactly what you said... The printer and the scanner are working correctly. Thank you

---

### Post by paul_mcl on 2009-08-09
```
$ ./install.sh 
ERROR: Unsuppored hardware platform "ppc", execution aborted
```

Shitty proprietary drivers.
Hope PPDs

```
$ find . -name *ppd*
./noarch/at_opt/share/ppd
```

will work.

---

### Post by paul_mcl on 2009-08-09
No, scx4200.ppd by itself doesn't want to work. This is what I got:

> Printer 'SCX-4200' requires the 'rastertosamsungspl' program but it is not currently installed.  Please install it before using this printer.

OpenPrinting database says the following:

> BW laser printer, max. 600x600 dpi, works Mostly 	
Recommended driver: splix2

> You now have an option between the experimental splix2 driver and the proprietary samsung driver. The splix2 driver appears to work just as well as the samsung driver. (26 November 2008) . Just grab the files, meet the dependencies (apt-get build-dep cups and libcups2/similar ) or using whatever package manager you have / methods. Then make install. It will appear in cups. Enjoy.

( [http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200) )

---

### Post by paul_mcl on 2009-08-09
Yep! Splix works perfectly. For printing, at least ;)
> Samsung SCX-4200, SpliX V. 2.0.0
As a test page got Ubuntu and lots of squares in grayscale :)
Use Free drivers, don't use the proprietary ones from Samsung.

---

### Post by giocarra on 2009-10-28
First of all : sorry for the way I intervene in this thread, hoping to be in the right section of the forum!
Second of all : I beg your pardon for my bad English.
And now let me expose my problem : 
last week I installed on a pc owned by my brother-in-law, Ubuntu Jaunty (09.04) and all gone fine. 
He has a Samsung SCX4200 multifunction printer so I used the suggestion exposed by yahs in this thread and all gone like a charm (Printer and also Scanner), but one thing : I'm not able to print an envelope, all kinds of envelopes.
When I try to print envelopes I receive this message (printed on the envelope itself) instead off the name of the sender and the name of the receiver :

```
"INTERNAL ERROR -uwaPaperSize[en_media][1] != (u16)(-1)
POSITION: 0x9b2575 (10167669)
SYSTEM :  : H6FW/xl_tbl
LINE :180
VERSION : QPDL 1.40 11-14-2005 "
```

I think this is an error due to software but the driver I installed is the last one (aug 2009) released from Samsung and, as I told before, printer and Scanner work very very fine.
Please note that with Windows Vista this does not succeed.
Does someone had my problem? And solved it?
I hope to receive from your courtesy a good suggestion about my problem.
Thanking in advance, best regards!
giocarra

---


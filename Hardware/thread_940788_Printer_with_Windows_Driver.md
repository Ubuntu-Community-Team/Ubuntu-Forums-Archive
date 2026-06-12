---
title: "Printer with Windows Driver?"
date: 2008-10-07
forum: Hardware
---

### Post by TriggerIsHappy on 2008-10-07
I have and Acer Aspire 5920 with Ubuntu Hardy and a Lexmark X2500 series printer. I was just wondering if there is a way for me to use the Window's driver in Ubuntu. I tried jusr running the CD in Wine and it could not find the printer connected via USB1. Is there a way to compile the files I need or something.

Thanks in advance,
Trigger

---

### Post by redbook4574 on 2008-10-14
I know this doesn't really help with your problem,but here goes
I tend to stick with HP printers/scanners/all in ones as Hp support linux
via hplip I don't know of any other manufacturer that does (I may be wrong).
As to windows printer drivers I have heard of an interface similar to ndiswrapper for printers but cannot be sure if it is any good. Perhaps somebody else has more experience of it.

---

### Post by stinger30au on 2008-10-14
heres a long shot


if oyu have your original xp install cd kicking round, install it in to ubuntu via virtualbox but use the closed source version as it allows ou to use the usb interface

so long as your printer is usb then you should be ok

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


go to the link above and follow the instructions to to install the closed source version.

then install xp and make sure to have the usb devices enabled

this sohuld alow xp to see the usb printer and install the drivers

you will also need a shared diretory between xp and ubuntu.

what your going to do now is in ubuntu anything you need printed you will save as a pdf file in to the shared directory

in xp you will need to install a pdf reader. i suggest foxitpdf reader as it is very small

[http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/)

install this to xp

now you can open the pdf files you created from ubuntu in the shared directory using xp and print them to the usb printer

---

### Post by BCPlanner on 2009-08-14
So, basically keep the Win-compatible printer, create whatever in Ubu (I'll be using 9.04), print-to-PDF, move the PDF into the Win environment and print from Win (I have new box with Vista and an older box with XP Pro).
 
Related Q: I have an old HP 5100C flatbed scanner (that probably is NOT supported by Vista but is barely supported by XP) - can I get scans into Ubu 9.04 via Win and the common Win/Ubu space? (I have not [yet] checked Ubu resources to see if there is an HP driver for this ancient device - an oldie but goodie.)
 
TIA
 
John Glenn
Hollywood/Fort Lauderdale FL
BCPlanner at gmail dot com

---

### Post by walt.smith1960 on 2009-08-15
Brother seems to do a decent job supporting Linux. I have a MFC-7820N printing & scanning. The only glitch I've found is if I put my Thinkpad R61 into suspend several times the printer driver can get really slow. Reboot and everything works again.

---


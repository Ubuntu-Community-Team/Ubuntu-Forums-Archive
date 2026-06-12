---
title: "c-80 printer recognized not printing."
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by metra on 2006-05-05
Hi, new to linux in general so if I need to do anything; compile or whatnot I need small words and cut-n-paste.

Okay, I'm using 5.10 and the setup was flawless and surprisingly quick, so kudos on that.

I added my printer through the system menu: System>Administration>Printing> New Printer

That part went fine, there was a driver for my Epson Stylus C-80 and it got its little icon as well.     When I print from Firefox or Office there is a job waiting for the printer.
I can also send out a test page and through the printer dialouge can see the jobs waiting.

The printer itself does nothing.  The light doesn't blink, the paper doesn't spool, nothing.

So, uh,m what can I do?

---

### Post by David Haas on 2006-05-12
metra--I see that Breezy does have a driver (PPD file) for the Epson Stylus c-80 (escp2-c80.ppd.gz) at /usr/share/cups/model/gimp-print/4.2. If it was selected correctly, then an unzipped copy should be in the directory /etc/cups/ppd. So, check in this directory  (go to this directory in the terminal and do an ls command there) for the file. Perhaps ubuntu didn't select this file correctly. If not, then you could select it yourself by clicking through the directories in the Gnome printing manager. 
David

---

### Post by metra on 2006-05-13
Thank you David.

Since I first posted and now I went into the point-n-click printing setup System>Administration>Printing and had removed and re-installed. That didn't work before, but I'll try it again now and see what happens.

I also just checked and I do have a PPD file for my printer. I'll see about getting a new file.

I don't know what the Gnome printing manager is right now, but I'll look it up and see if I can figure out how to reinstall the file.

Again, thanks for responding.

---

### Post by metra on 2006-05-14
Okay, I'm assuming that the Gnome printing manager is the thing I was using.

I tried just removing and reinstalling the printer and this time I noticed something weird. 
1. It doesn't automatically detect the printer so I have to specify the port.
2. It has shows 3 "Parallel Port #1".  One of which has (epson) beside it.
3. My printer is hooked up through a USB port.  All the USB ports show nothing.

I went ahead with the re-installation and same problem.

---

### Post by metra on 2006-05-14
YEY! I can print!

I went into Synaptic and re-installed the Gnome printing manager.  Actually, I re-installed everything that came in up in the search for print and manager. 26 things were re-installed.  I have no idea which one was the one that wasn't in right.

But I can print now!:KS

---

### Post by David Haas on 2006-05-14
Well-done Metra! There must have been something wrong with the default installation of the Gnome printing manager.  
David

---


---
title: "Print via ethernet to Apple printer"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by Autolycus on 2006-01-11
Howdy...

Ubuntu 5.10 loaded on a PC...networked with another PC (Windows XP) and a Macintosh (OS 9.2.2). Also on the network is an Apple Laserwriter 4/600 (this is a postscript printer).  Is it possible for the Ubuntu computer to print to the Apple printer?

TIA,

Ken

---

### Post by tim15856 on 2006-01-12
I'm not at home, so I can't check to see if Ubuntu has the drivers built in. See if this helps any. [http://www.linuxprinting.org/show_printer.cgi?recnum=Apple-LaserWriter_4_600](http://www.linuxprinting.org/show_printer.cgi?recnum=Apple-LaserWriter_4_600)

---

### Post by Autolycus on 2006-01-12
Thanks....I'll give it a try this weekend..

---

### Post by mpvano on 2006-01-17
Just a note about problems I've had with similar printers:

There seems to be a bug in the CUPS printer setup. It gets very confused by printers whose names contain slashes because it uses the name in ways like a pathname is used.

To handle this, CUPS is SUPPOSED to internally replace the slashes with underscores, but somewhere, something between gnome's applets and CUPS is dropping the ball during the installation. The installation of such a printer will appear to work, but all printing will silently fail (although there's an entry in the CUPS log file indicating each failure).

If you should encounter this problem, the fix is very simple - using sudo, edit the file /etc/cups/printers.conf. Look for all occurences of the printer name and make sure that the following TWO changes are made to them:

    - all underscores need to be changed to dashes (go figure!)
    - all slashes need to be changed to underscores

For example, for my LaserWriter_16/600, the corrected name needs to be LaserWriter-16_600.

It looks like someone got too clever for their own good by trying to assume that all pdf printer names could be directly used as pathnames. They then tried to fix it by replacing the slashes with underscores, but then discovered that some printer names have underscores in them! At this point, the code is probably a hopeless mess.....

I hope you don't have trouble, but if you do, this will probably fix it.

One more problem you may have is that older printers obviously don't support postscript 3, but somebody apparently didn't get the memo about that, and so you may have to reconfigure the driver options NOT to ever send any to your printer. Here's the fix for that....

In the printer properties dialog's "advanced" tab, make sure you set the popup to indicate "Convert to PS level 2" if you have a printer like that.

If you're not sure you need to do this, you'll know right away if the printer begins spewing error pages....

Mario

---


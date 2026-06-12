---
title: "dual boot, xp on usb hard drive"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by SirThom on 2008-03-15
OK, here is the deal.  I have an hp pavillion tx1000nr.  I bought it about a year ago to get a linux distro running on it, gave up after a while, purchased and installed XP (to get rid of that rubbish vista) and have been tolerating that for a while.
Recently while doing a search I found a page filled with information on unstalling ubuntu on that line of machines.  I'd like to give it another go, but since I have had XP for a year, set up lots of stuff in it, bought some shareware, etc, I don't want to give that up completly.
I already tried deleting stuff I didn't need, defragging, and then using the gibbon disc to create a partition for dual booting.  It didn't work.  There wasn't a large enough gap of space.
So, I dropped some cash on a 160 GB Western Digital Passport hard drive.  After some fits and starts (this is a machine that tends to overheat sometimes) I was able to clone my entire hard drive to this USB hard drive.  I set the bios to boot first from the USB drive.  When the computer complained, I even put together a lovely boot.ini file on the drive.  Basically my goal is to have my machine be primarly an ubuntu machine, and when I want to access XP I reboot after plugging in this sexy little black hard drive.
So, I notice that when it goes to the USB drive initially, to run the boot.ini file for example, it ultimatly runs the copy of Windows on the main hard drive.  Well, I want to get rid of that copy of Windows.  So, I was trying to force the computer to use the copy on the external drive, and I physically removed the main hard drive and booted with only the USB hard drive plugged in.  This is what I got:

Windows could not start because of a computer disk hardware configuration problem.
Could not read from the selected boot disk.  Check boot path and disk hardware.
Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.

Sooooo, I'm not sure what to do at this point.  I've seen several web pages that have said that it's as simple as cloning the drive, setting the BIOS, and that's that.  It's not working.

I hope you guys don't mind an XP question on an ubuntu forum, but I'm doing this so that I can install ubuntu and I'm sure that many other people here have tried or have done the same thing.

Cheers,
-Thom

---

### Post by balloons on 2008-03-15
Possible - follow this guide

[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

---

### Post by SirThom on 2008-03-15
> **guitara said:**
> Possible - follow this guide

[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

Awesome, thanks, I'll try it.  I was hoping to not have to reinstall everything fresh and redo all the little system mods, but I think that the end result will be the same.

---

### Post by SirThom on 2008-03-16
> **guitara said:**
> Possible - follow this guide

[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

Success,  Thanks a lot.  I am migrating everything over and soon I am installing ubuntu.

---


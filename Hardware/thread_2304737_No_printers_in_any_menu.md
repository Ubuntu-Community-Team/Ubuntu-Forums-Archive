---
title: "No printers in any menu"
date: 2015-11-29
forum: Hardware
---

### Post by Evil Wayz on 2015-11-29
I have a fresh install of 14.04.  THere is no option on any of the menu for the CUPS front end.  I even tried editing hte menus to see if it was unchecked.  Ubuntu Software Center says it is installed.  How do I access it, or better yet, how do I add it to the preferences menu where it goes?  Incidentally, it works, I just scanned something with it.

---

### Post by kurt18947 on 2015-11-29
What happens if you tap the Super (windows) key and type 'print'? I don't have Ubuntu installed but I think it's pretty similar to Ubuntu-Gnome. If you have your printed connected via network, you may see need to click 'networks' as well. You could also type "localhost:631" in the browser address bar and work from there. I've not had much success with that but others have.

---

### Post by brianewalsh2 on 2015-11-30
What make is your printer? Some manufacturers are producing linux front ends, you just have to search. I know that for my Brother printer there was two .deb packages  I had to source from their site and ubuntu notices it and it works flawlessly.

---

### Post by Evil Wayz on 2015-11-30
I have a very old printer, it is a Lexmark 1100.  Lexmark doesn't even make drivers for it anymore.  But that still doesn'
t explain why i don't have a printers option under preferences. I'm running 14.10 off a usb stick on my laptop and it has that option.

---

### Post by philinux on 2015-11-30
What happens if you type print in Dash. 

Also I remember from old that lexmarks and brother could be classed as a house brick in Linux. But you never know.

---

### Post by kurt18947 on 2015-11-30
> **philinux said:**
> What happens if you type print in Dash. 

Also I remember from old that lexmarks and brother could be **classed as a house brick in Linux.** But you never know.

That's what I recall as well. There were at one time linux drivers around for Lexmark Inkjets but they were scarce and not well supported. Lexmark business class laser printers on the other hand are supported. I had a Lexmark Z55 inkjet printer many years ago. Lexmark's web site still recognizes the model. The only linux support available is for Caldera. Caldera? Also, I believe Lexmark will be ceasing production of ink cartridges soon, if they haven't already.  They stopped producing new inkjet printers in 2013 I think. Current production laser printers seem to have reasonable linux support.

Edit: Here is a post from 2004 on installing an X1100 series printer. I have no idea if the package mentioned is available.
[http://ubuntuforums.org/showthread.php?t=5496](http://ubuntuforums.org/showthread.php?t=5496)

---

### Post by efflandt on 2015-12-01
To do any administrative tasks in cups from [http://localhost:631/](http://localhost:631/) I think you have to add yourself to lpadmin group.

I used to have an old Lexmark inkjet that I think was Windows only (totally raster graphics, not even any built-in text mode, could not be network shared even in Windows). But Lexmark laser printers do postscript or HP PCL, so they are easily supported. I currently have a C543dn duplex color laser (that worked with C534 driver before Ubuntu had C543 driver) and X204n all in one which substituted for a broken down HP LaserJet at work by simply matching its IP address (no driver changes needed) until we got a new HP printer. Lexmark had a .deb scanner driver for the X204n and other X models (newest one was for Ubuntu 12.04) which works in 14.04 with xsane.

---


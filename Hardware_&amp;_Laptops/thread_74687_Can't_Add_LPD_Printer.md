---
title: "Can't Add LPD Printer"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by metrounit9 on 2005-10-12
Can't add an 'LPD' networked printer using the Gnome Printer Configuration app (System > Administration > Printing > add printer)

I complete the first of two steps (select LPD, enter host 192.168.0.1, and port lp) when I click next the app hangs for about 30 seconds before closing and sending me back to the 'add printer' icon.

I can set-up CUPS, HPDirect printers with no configuration problems...other than I can't print anything. I have used the 'LPD' option on FC2 and Suse with no problem that's why I wanted to use it on Ubuntu.

Here's my hardware:
Printer: HP LaserJet 4 Plus
Printer Server: D-LINK 704P router with printer parallel port (lp)

I can print to this printer with no problems with Win XP on the same network.

Any suggestions would be appreciated.

---

### Post by FRAMBO on 2006-10-11
Same problem here with same router.  The port queue is not retained.  ](*,) 

I had this printer working in Kubuntu.  Did you find a solution?

---

### Post by FRAMBO on 2006-10-11
Found fix here: [http://ubuntuforums.org/showthread.php?t=26226&highlight=lpd+printer](http://ubuntuforums.org/showthread.php?t=26226&highlight=lpd+printer)



Sounds like a simple bug to be fixed in the interface.

---


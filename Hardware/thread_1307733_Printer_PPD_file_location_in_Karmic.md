---
title: "Printer PPD file location in Karmic"
date: 2009-10-31
forum: Hardware
---

### Post by Manyette on 2009-10-31
Hi All, Installed Karmic, Default hplip 3.9.8.  hp-setup says cannot find correct PPD files for HP J6480 printer.  Retrieved files from Jaunty backup, but can't find out where to locate them.  No matter where I try, hp-setup says no file or incorrect file.  In Jaunty the location was /etc/cups/ppd.  I have tried other locations, based on where karmics ppd files are kept, but hp-setup says no file or incorrect file no matter what. Any ideas?  Thanks for any advice.  Don

---

### Post by silver1973 on 2009-10-31
same exact problem. help?

---

### Post by ubutufan on 2009-10-31
The ppd files are in /etc/cups/ppd.

I can see mine for sure.

---

### Post by Manyette on 2009-11-01
Silver1973, After all my grief trying to get the printer to work, the answer was too simple for me to find.  If you are running 9.10, try the following.  Select Administration -> Printing, and when the box appears, select New at the top of the box.  From there the prompts will lead you throught the installation of your printer hopefully.  At least, it did work for me and the printer is now installed. It even found and enabled the duplexer on my printer, which I had difficulty getting working prior to this.  I hope it works as well for you.  Regards. Don

---


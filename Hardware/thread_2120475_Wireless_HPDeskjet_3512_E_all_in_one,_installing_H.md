---
title: "Wireless HPDeskjet 3512 E all in one, installing HPLIP"
date: 2013-02-26
forum: Hardware
---

### Post by oldfiddler68 on 2013-02-26
Trying to install HP Deskjet 3512 E all in one printer and got to this message after many tries.  I want to use this printer as a wireless printer which is already setup with its own i/p address when it works with a windows machine.


[B]Installation Wizard

You have selected Ubuntu 12.04 using the HP Deskjet 3512 E-all-in-one.

Ubuntu 12.04 supplies HPLIP 3.12.2 and it does  not support your printer.

You must download and install HPLIP in order to use your printer with Ubuntu 12.0 4.[/B]

Is this telling   my printer is not supported or that I need to download a different HPLIP.
Because I have downloaded hplip-3.13.2 which I hope has what I need. How do I install this new file? Am I headed in the right direction.

---

### Post by Cuba71 on 2013-04-12
Deleted

---

### Post by agillator on 2013-04-12
According to HPLIP ([http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3510_series.html)) the 3510 series (including the 3512) is fully supported. Try purging the Ubuntu provided HPLIP, download directly from HP ([http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)) and install that one. Remember it may recognize your printer as a '3512' or as a '3510 series' printer.

---

### Post by Cuba71 on 2013-04-13
compilation failed with this error

In file included from prnt/hpcups/HPCupsFilter.h:34:0,
                 from prnt/hpcups/HPCupsFilter.cpp:33:
prnt/hpcups/CommonDefinitions.h:43:25: fatal error: cups/raster.h: No such file or directory
compilation terminated.
make: *** [hpcups-HPCupsFilter.o] Error 1

---

### Post by Cuba71 on 2013-04-13
Was able to install HPLIP-3.13.4.  Still nothing happens

**_Update_** Re-installef HP 3512 all-in-on using HP 3520 driver, and it prints, but the scanner is not recognized

**_Latest Update:_** Upgraded from 12.10 to 13.04, deleted and re-installed the printer with HP 3510  drivers, and now it prints and scans the way it should. Working on the wireless features.

---

### Post by EliteNeophyte on 2013-04-15
> **agillator said:**
> According to HPLIP ([http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3510_series.html)) the 3510 series (including the 3512) is fully supported. Try purging the Ubuntu provided HPLIP, download directly from HP ([http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)) and install that one. Remember it may recognize your printer as a '3512' or as a '3510 series' printer.

I came here having the same problem as OP, near as I can tell those links are dead, every time I try anything from hplipopensource they 404

---

### Post by EliteNeophyte on 2013-04-15
> **EliteNeophyte said:**
> I came here having the same problem as OP, near as I can tell those links are dead, every time I try anything from hplipopensource they 404

I found the sourceforge page where the project is actually stored so lucky us **here you go **[http://sourceforge.net/projects/hplip/?source=dlp](http://sourceforge.net/projects/hplip/?source=dlp)

---

### Post by Cuba71 on 2013-04-15
I was able to download **hplip-3.13.4.tar.gz** from that site before it died.
I'd wish there was a way to forward it to you.
That and an upgrade to Ubunto 13.04 is what I used to make it work.

---

### Post by EliteNeophyte on 2013-04-15
No worries, like I said I found the sourceforge page

---


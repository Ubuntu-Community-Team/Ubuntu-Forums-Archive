---
title: "Printer Canon Pixma MG6250 fails with large photos"
date: 2015-01-24
forum: Hardware
---

### Post by MagnusL on 2015-01-24
Hi!

I have a Canon Pixma MG6250 printer, working nicely with W8, but when I try to print lagre photos from Ubuntu, it fails. At least sometimes it works printing smaller (10 x 15 cm). The printing process starts in Gwenview or Digicam, and then processes nicely. The printer says "Processing" and then, after a while, just returns to a ready state. I have tried with several ubuntu computers, running 13.04, 13.10, 14.04 and 14.40. I've tried several versions of the driver supplied in the list (adding printer i kubuntu or Unity). I should say that the printer did work, printing A4 photos, as late as december. Is there any update that might have caused this, or am I experiencing intermittent problems (it takes a long time to diagnose this, as one attempt to print might last 10 minutes, so I'm feeling quite lost).

I have tried the driver from Canon, at [http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG6250.aspx?type=download&softwaredetailid=tcm:13-863349&os=Linux&language=](http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG6250.aspx?type=download&softwaredetailid=tcm:13-863349&os=Linux&language=). Running the install.sh here, provides me the output: 

magnus@vista6:~/Downloads_done/cnijfilter-mg6200series-3.60-1-deb$ ./install.sh
==================================================

Canon Inkjet Printer Driver
Version 3.60
Copyright CANON INC. 2001-2011
All Rights Reserved.
                                                                                                                                                                 
==================================================                                                                                                               
An error occurred. The package management system cannot be identified.        

So: anyone got any ideas on this?

Best, 


Magnus

---

### Post by pdc on 2015-01-24
Hi Magnus

> An error occurred. The package management system cannot be identified.         ........folks think this happens if the install script gets a whiff of an rpm package on your debian based system; I don't know if that could be the case for you;

________________

what the install script does is look to see if you have 32bit or 64bit; and if you are debian or rpm; so one can easily do the install in a more manual way;

There is a folder called [COLOR="#008000"]Packages[/COLOR] inside the main folder of [COLOR="#008000"]cnijfilter-mg6200series-3.60-1-deb[/COLOR]

............ there will be a COMMON package and a specific one; for both 32bit and 64bit: install the COMMON one first; then the specific; of the type appropriate for you; ie 32 or 64bit; 

you should be able to install by right-clicking on the packages; and selecting install with ubuntu center or double-clicking on them; or command line ```
sudo dpkg -i whatevertherightnameis.deb
```

---

### Post by MagnusL on 2015-01-24
Hi!

Thanks, didn't realize I could do it manually. 

However, I get a dependency error when installing the second package (cnijfilter-mg6200series_3.60-1_i386.deb ). It needs libtiff4, and I seem not to have nor be able to install it. I have libtiff5, however. I notice that this driver is from 2011, so maybe it is a bad idea altogether to try to install it?

Magnus

---

### Post by pdc on 2015-01-26
Hi Magnus;

my apologies for delay in replying; 

easy to install libtiff4; definitely the thing to do so go here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) to the main Debian repository and go about 14 or 17 down the list and click to the download the 32bit or 64bit that you need; (you can see the first dozen or so on the list are libtiffdev which you don't want ..............)

once libtiff4 is installed, do re-run the install script and it should all go fine;

____________

Ubuntu took away libtiff4 for some reason a couple of releases ago; the Canon drivers < version 4.0 needed libtiff4 so the above is to way to fix the issue

---


---
title: "Trying to get Epson R380 and Gutenprint Working"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by richardq on 2007-07-22
I've got an Epson Stylus Photo R380 printer and I'm trying to get it working under Feisty.

Based on what I've read, the most recent Gutenprint versions contain drivers for this printer, but the Feisty repo's don't have these yet. 

I've followed the instructions from Gutenprint on downloading and compiling their latest sources. This went successfully. I then restarted the machine and when I add a new printer, the R380 is still not on the list, even though the version I dowloaded is supposed to have R380 drivers.

Any clues on how to get gutenprint working? 

I also read in their literature that their package supplies a Gimp enhanced printing plugin. I see no evidence of this either. How do I select that customized printing dialog? The gimp printing dialog looks the same as it always has.

Any help would be greatl appreciated.

RQ

---

### Post by linuxwizard on 2007-07-22
According to this that printer is not supported. Scroll down the page to your model. Supported printer has a link.
[http://www.openprinting.org/show_driver.cgi?driver=gutenprint&fromprinter=Epson-Stylus_Photo_R350](http://www.openprinting.org/show_driver.cgi?driver=gutenprint&fromprinter=Epson-Stylus_Photo_R350)

Here I don't see R380 printer listed
[http://www.openprinting.org/printer_list.cgi?make=Epson](http://www.openprinting.org/printer_list.cgi?make=Epson)

Where you got the drivers I would check to make sure that they are for a R380 and will work.

---

### Post by joncrlsn on 2007-08-09
The previous commenter linked to openprinting, not gutenprint documentation.  This gutenprint release doc says the R380 is supported in the development version:  [http://sourceforge.net/project/shownotes.php?release_id=509939&group_id=1537](http://sourceforge.net/project/shownotes.php?release_id=509939&group_id=1537)

Did you have any luck in getting the R380 to show up?  I've installed gutenprint 5.1.3 and can't get the RX580 to show up either.

---

### Post by linuxwizard on 2007-08-10
joncrlsn

OpenPrinting is the best source to use to find if a printer is supported or unsupported. It also shows RX580 as unsupported.

---


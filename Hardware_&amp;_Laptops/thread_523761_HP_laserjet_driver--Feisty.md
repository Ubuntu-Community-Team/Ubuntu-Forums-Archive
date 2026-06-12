---
title: "HP laserjet driver--Feisty"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by radiors on 2007-08-12
I have an HP 3700n color Laserjet.   The printer is connected as a network printer with a static IP address.  

This printer worked great under Dapper.  But after I upgraded to Feisty (clean install) the postscript driver no longer works correctly.  When I print a test page the printer just spits out blank or cryptic pages one after the other until I cancel printing.  I have tried downloading a fresh ppd file and installing it, but I can't get past the screen that says the ppd is already installed for this printer.  There is no option to overwrite the existing ppd.

I have had some very limited success using the hpijs driver, but I get frequent "out of memory" errors on the printer.  This is ridiculous because the  document is small and there is tons of memory for it.  I even get "out of memory" on the test page.

I have tried removing and reinstalling the printer many times with no joy. 

Any ideas would be greatly appreciated.

Thanks.

---

### Post by 1/0 on 2007-08-12
I would first uninstall hpijs/hplip and remove the PPD (remove the foo2zjs folder if you installed one.) Uninstall Cups. Then I would reinstall Cups using for instance [this guide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29") Just so you don't miss anything. 

Try using a different PPD if its been damage. Try one from [http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_3700](http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_3700) for instance.

---


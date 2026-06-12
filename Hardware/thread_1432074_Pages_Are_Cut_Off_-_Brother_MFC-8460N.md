---
title: "Pages Are Cut Off - Brother MFC-8460N"
date: 2010-03-17
forum: Hardware
---

### Post by aramodo on 2010-03-17
Hi Everyone,

Having some trouble with my Brother MFC-8460N. Every page I print is about 4 inches too low on the page, so the bottom is cut off. This happens no matter what program I print from (Openoffice, Print Test Page, gedit, firefox, etc.)

I have tried uninstalling the printer and reinstalling it with the PPD file from Brother.

I also went into synaptic and installed "brother-lpr-drivers-laser" and "brother-cups-wrapper-laser," but now I can't find out where those drivers were installed... how can I use them? They don't show up in the "add a printer" wizard.


Any help would be appreciated..

Thanks,
Matthew

---

### Post by chehalem on 2010-04-08
Hi 

had the same problem but finally found solution

go to [http://localhost:631/printers/](http://localhost:631/printers/)

your printer should show up. click on it. 

go into administration - modify printer

click continue twice until it comes to current drivers page.
for some reason even though I downloaded the two specific ones for the mfc-8460n it said that i was using the mfc-8440 driver.

if you already downloaded the correct ones from the brother website [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html) 

they should be somewhere at the bottom of the long list of drivers.  click on it to change driver.  print a test page.  should be good to go if it was same problem as me.

---


---
title: "[SOLVED] Updated Open Office from 2.4 to 3.0 but 2.4 remains?"
date: 2008-11-27
forum: General Help
---

### Post by elanning on 2008-11-27
Greetings,

I just attempted to upgrade open office from 2.4 to 3.0.  I got the repositories added, and the system update manager listed open office as one of the newly available updates, and everything seemed to download and install.  But when I start up any of the OO applications its still version 2.4 somehow  :confused:  I am relatively new to linux so I do not know how to go about troubleshooting this issue.  

Please help! 

Thanks.

---

### Post by virx on 2008-11-27
Could it be that package debian-menues or something like this is missing? It adds new OO3 to the menu.

Do you want to remove 2.4?

---

### Post by TeXtonyx on 2008-11-27
This is how I did it and don't forget the last step.

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

"With that done you should have just one thing left to do: 
Install the desktop integration package. That should be in the 
DEBS folder: 

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

If everything works out you should be able to open 
OpenOffice.org 3.0 from the Applications menu on your desktop."

---


---
title: "Data Souces disappeared from Open Office Writer"
date: 2008-11-24
forum: General Help
---

### Post by PeggySue on 2008-11-24
Hi,

A while back I upgraded to Ubuntu 8.04 which comes with Open Office 2.4.

I now can't print labels because the "Data Sources" option doesn't appear in the "View" menu with this version.

I need a quick fix and a long term solution.  Any ideas would be most welcome.  My Plan B is go to a friend still using windows but you can image I am not too keen on that!!

---

### Post by TeXtonyx on 2008-11-24
> **PeggySue said:**
> Hi,

A while back I upgraded to Ubuntu 8.04 which comes with Open Office 2.4.

I now can't print labels because the "Data Sources" option doesn't appear in the "View" menu with this version.

I need a quick fix and a long term solution.  Any ideas would be most welcome.  My Plan B is go to a friend still using windows but you can image I am not too keen on that!!

I just upgraded to OpenOffice 3.0 and since I'd never used the
View -> Data Sources before, I decided to test it. There is
currently a thread on 'how to upgrade to OOo 3' on the forum

---

### Post by PeggySue on 2008-11-24
Hi TeXtonyx

I have found the post that explains how to add Open Office to the repositories so I will do that.

[http://ubuntuforums.org/showthread.php?t=987695&highlight=upgrade+open+office]("http://ubuntuforums.org/showthread.php?t=987695&highlight=upgrade+open+office")

Many thanks.

---

### Post by PeggySue on 2008-11-24
DISATER!!!!!!!!!!!!

Open Office upgrade failed. 

The error messages are:
/usr/lib/openoffice/program/soffice: 237: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 254: /usr/lib/openoffice/program/soffice.bin: not found

The package manager can't fix it as it says there are conflicts.

OpenOffice has disappeared from my system.  Anyone any ideas how to reinstall Open Office?

---

### Post by PeggySue on 2008-11-24
SORTED!!!!!!!!!!!!!

I had to remove OpenOffice.org-bas-core and download version 3 from the open office site and install it by hand.

Not impressed with the package manager

---

### Post by TeXtonyx on 2008-11-24
Well, if you did this manually, then don't forget this step.

-----------------------------

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

If everything works out you should be able to open OpenOffice.org 3.0 
from the Applications menu on your desktop.

------------------------------

I had to install the sun java jre, maybe you already have that.

java -version

and with Firefox for example open about: plugins (no space after the :

I'm not sure it's necessary, but I watched the debs install and
saw an error message about the En-dict needing java jre. 

[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

This is where I downloaded the .deb.tar.gz for 8.04 English and
it has about 30 other languages available.

---

### Post by PeggySue on 2008-11-24
Thanks for that.

I have installed the desktop integration and it opens from the applications menu.  Writer appears to work OK and I have done the labels.

I will check java.jre later; I am printing 100 copies of a newsletter at the moment and have had enough go wrong for one day!!

Thanks for your help.

---


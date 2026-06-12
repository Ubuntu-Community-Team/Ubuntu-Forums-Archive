---
title: "how to update OpenOffice from 2.4 to 3.0 in Ubuntu 8.10"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by mamous on 2008-12-03
Hi this is the how u can update open office in an easy way.

[COLOR="Red"][SIZE="5"]1-[/SIZE][/COLOR] you have to download the DEB from [[COLOR="DarkGreen"][SIZE="3"]open office[/SIZE][/COLOR]]("http://download.openoffice.org/other.html#en-US") site.
[COLOR="Red"][SIZE="5"]2-[/SIZE][/COLOR] Extract the tar.gz archive in your desktop.
[COLOR="Red"][SIZE="5"]3-[/SIZE][/COLOR] go to terminal and by this command
> sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/*.deb
[SIZE="5"][COLOR="Red"]4-[/COLOR][/SIZE] you have to remove the old version of open office by this command
> sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
[COLOR="Red"][SIZE="5"]5-[/SIZE][/COLOR] you have to install the package that provides menu items for OpenOffice 3.0 by this command
> sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb



[CENTER]-_-_-_-_-_-_-_-_-_--_-_-_-_-_-_-_-_-_--_-_-_-_-_-_-_-_-_-[/CENTER]

[COLOR="Red"][SIZE="5"]*[/SIZE][/COLOR] If you changed your mind you can remove Open office by this comand
> sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure




I hope you like it

---

### Post by x58 on 2008-12-04
Works like firework. Thanks, was very helpful

---

### Post by nygamma on 2008-12-05
This seems to be working. Many thanks from me, as well.

---

### Post by Liunx on 2008-12-05
Can  the ubuntu teak help us to get the lastest office?
):P

---

### Post by cymrujmc on 2008-12-05
Worked perfectly!! Third or fourth how-to I've tried for this.  Thanks!:D

---

### Post by ceasol on 2008-12-06
Update OO 3 was a breeze!!!

---

### Post by inobe on 2008-12-06
or you can follow this tutorial

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

and if you are running a 64bit system, get the tar.gz here

[ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz/)

---

### Post by Ziyan Junaideen on 2009-03-09
This is not update, but install. You can update your existing OO 2.4 to OO 3.0 from the Update Manager.

The steps required are found [here]("http://linux-sri-lanka.blogspot.com/2009/02/updating-openofficeorg-24-in-ubuntu-to.html").

( [http://linux-sri-lanka.blogspot.com/2009/02/updating-openofficeorg-24-in-ubuntu-to.html](http://linux-sri-lanka.blogspot.com/2009/02/updating-openofficeorg-24-in-ubuntu-to.html) )

---


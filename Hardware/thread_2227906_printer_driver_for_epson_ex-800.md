---
title: "printer driver for epson ex-800"
date: 2014-06-04
forum: Hardware
---

### Post by jgw on 2014-06-04
I have an epson ex-800 printer and I need to find a driver for it.  Its an all in one printer but I only need the driver for the printer section (the rest would be nice but not necessary).  There is a long list of epson printer drivers and I am sure one of them would work just fine but I have no idea which one.  If anybody has a clue on this one it would be appreciated.  I know there is also a generic available but it doesn't work all that well.

Thank you..........

---

### Post by pdc on 2014-06-04
Help us understand what your device is

> I have an epson ex-800 printer and I need to find a driver for it. Its an all in one printer 

If I google on ex-800, I get this [http://www.epson.com/cgi-bin/Store/ProductQuickSpec.jsp?BV_UseBVCookie=yes&infoType=Related&BV_EngineID=ccchadgdeljhgficfngcfkmdhjidfmh.0&oid=8362&BV_SessionID=%40%40%40%400554764630.1401913730%40%40%40%40&nextPage=%2fBackCatalog.jsp&BV_UseBVCookie=yes&query=](http://www.epson.com/cgi-bin/Store/ProductQuickSpec.jsp?BV_UseBVCookie=yes&infoType=Related&BV_EngineID=ccchadgdeljhgficfngcfkmdhjidfmh.0&oid=8362&BV_SessionID=%40%40%40%400554764630.1401913730%40%40%40%40&nextPage=%2fBackCatalog.jsp&BV_UseBVCookie=yes&query=)

a dot-matrix that was discontinued in 1989

(have a read at the side of your machine)

we can point you to the correct drivers; Epson make a lot with names like SX-800      and XP-800 and such like

---

### Post by sammiev on 2014-06-04
> **pdc said:**
> Help us understand what your device is



If I google on ex-800, I get this [http://www.epson.com/cgi-bin/Store/ProductQuickSpec.jsp?BV_UseBVCookie=yes&infoType=Related&BV_EngineID=ccchadgdeljhgficfngcfkmdhjidfmh.0&oid=8362&BV_SessionID=%40%40%40%400554764630.1401913730%40%40%40%40&nextPage=%2fBackCatalog.jsp&BV_UseBVCookie=yes&query=](http://www.epson.com/cgi-bin/Store/ProductQuickSpec.jsp?BV_UseBVCookie=yes&infoType=Related&BV_EngineID=ccchadgdeljhgficfngcfkmdhjidfmh.0&oid=8362&BV_SessionID=%40%40%40%400554764630.1401913730%40%40%40%40&nextPage=%2fBackCatalog.jsp&BV_UseBVCookie=yes&query=)

a dot-matrix that was discontinued in 1989

(have a read at the side of your machine)

we can point you to the correct drivers; Epson make a lot with names like SX-800      and XP-800 and such like

Made my day when I seen printer drivers for this model only go up to Windows98.

---

### Post by jgw on 2014-06-04
Boy!  Talk about screwing up!  My printer is an XP-800!!!  (reasonably new) <G>  My apologies to one and all (currently hanging my head in utter shame)

---

### Post by sammiev on 2014-06-04
Go [here]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") and type XP-800 in the search bar and select Linux in the drop down box.

---

### Post by pdc on 2014-06-05
you should end up here.........the full feature driver page [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18782&DSCCHK=1656158aae493417d004b0d5801c13d672b30c9a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18782&DSCCHK=1656158aae493417d004b0d5801c13d672b30c9a)

Ubuntu uses debian packages; so you need those; epson-inkjet-printer-201208w_1.0.0-1lsb3.2_i386.deb or epson-inkjet-printer-201208w_1.0.0-1lsb3.2_amd64.deb

you need to work out if you have 32bit or 64bit system; > uname -a in a terminal should tell you;

when you click to download, your system may offer to OPEN or INSTALL with ubuntu software centre or gdebi installer: accept that kind offer and it should create a printer driver

_____________

Epson make iscan available to drive the scanner on your device

---


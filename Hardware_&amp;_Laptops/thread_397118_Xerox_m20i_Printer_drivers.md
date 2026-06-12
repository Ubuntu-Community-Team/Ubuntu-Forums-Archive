---
title: "Xerox m20i Printer drivers"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by 2ol on 2007-03-30
Where Can i get driver for Xerox m20i Printer for Ubuntu 6.10?

---

### Post by ramjet_1953 on 2007-03-31
If you go here:

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=M20_M20I&Xlang=en_US&Xcntry=USA&prodName=WorkCentre%20M20/M20i](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=M20_M20I&Xlang=en_US&Xcntry=USA&prodName=WorkCentre%20M20/M20i)

I believe you will find a linux driver.

Regards,
Roger 8)

---

### Post by daybreaker on 2007-08-20
there is no longer a linux driver listed there... any other ideas? anyone?

---

### Post by daybreaker on 2007-08-20
Solved...

Using the PCL6 driver suggested by linuxdrivers.org wasnt working for me (Idont know if it's because the m20i is a network printer, or what)

Anyways, when I was trying to find drivers for our other printer (a xerox phaser 7750gx) I found a PPD tar file with linux drivers for several xerox printers... And not only was the 7750GX among them, but so was the m20 ppd that is missing from Xerox's official m20i page.

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=7750&Family=Phaser&ripId=&langs=English%20(US)&plats=Windows%20Vista%20x64,Windows%20Vista,Windows%20Server%202003%20x64,Windows%20Server%202003,Windows%20XP%20x64,Windows%20XP,Windows%202000,Windows%20Me,Windows%2098,Windows%2095,Windows%20NT%204.0,Windows%20NT%203.5x,Windows%203.1x,Windows%203.x,MS-DOS,Macintosh%20OS%20X,Macintosh%209,Macintosh%208,Macintosh%207,UNIX,IBM%20OS/2,IBM%20AS/400&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=7750&Family=Phaser&ripId=&langs=English%20(US)&plats=Windows%20Vista%20x64,Windows%20Vista,Windows%20Server%202003%20x64,Windows%20Server%202003,Windows%20XP%20x64,Windows%20XP,Windows%202000,Windows%20Me,Windows%2098,Windows%2095,Windows%20NT%204.0,Windows%20NT%203.5x,Windows%203.1x,Windows%203.x,MS-DOS,Macintosh%20OS%20X,Macintosh%209,Macintosh%208,Macintosh%207,UNIX,IBM%20OS/2,IBM%20AS/400&Xtype=download&uType=)

---

### Post by Aeo76 on 2008-05-02
Not to be a total newbie here - but /usr/share/cups/<model>/ is a bit different from Ubuntu's setup.

Where should the driver folder be copied?

---


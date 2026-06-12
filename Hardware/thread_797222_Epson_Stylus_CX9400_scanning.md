---
title: "Epson Stylus CX9400 scanning"
date: 2008-05-17
forum: Hardware
---

### Post by fdhionly on 2008-05-17
I can't set up my new multifunction scanner, an Epson Stylus CX9400 to scan.  Any suggestions on what I need to try?  Thanks

Note, I was able to solve this using the documentation on Scanners on the Ubuntu website.

---

### Post by komputes on 2009-07-23
I had the same issue, and found the fix here: [http://ubuntuforums.org/showthread.php?t=846077](http://ubuntuforums.org/showthread.php?t=846077)

To fix, open a terminal and run
```
sudo apt-get install libsane-extras
```

restart and open xsane or gimp and scan to your hearts content!:popcorn:

---

### Post by erikthedrink on 2011-01-23
I had ubuntu 10.04.  I went to the ubuntu site and dowloaded the .iso for ubuntu 10.10.  I burned the .iso to a CD-ROM.  I installed it.  I manually shut it off after two hours.  When I checked Applications, Graphics, I found Simple Scan.
It didn't recognize my scanner, after I turned it on.  It recognized my printer.  I shut down the Simple Scan application and restarted the application.  I pressed Scan and I heard the scanner of my CX7400, not 9400, hum to life.  It scanned the image.  I easily cropped it.  I rotated it twice and saved it.  I opened the file under the default jpeg viewer.  The file is great.  I wish ubuntu 10.10 was available from the Update Manager, yet I am very happy to have use of my scanner with Ubuntu 10.10.  I believe this distribution is known as Maverick Meerkat.

---


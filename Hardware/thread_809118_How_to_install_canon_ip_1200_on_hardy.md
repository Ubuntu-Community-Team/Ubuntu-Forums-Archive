---
title: "How to install canon ip 1200 on hardy?"
date: 2008-05-27
forum: Hardware
---

### Post by RalfWawo on 2008-05-27
dear all, i've been using canon ip 1200 on windows for my printing devices. now, i'm migrating to ubuntu. i want to use the printer also in this operating system, but i found difficulities on installing the driver software. please help.thank you all and GBU:confused:

---

### Post by gary4gar on 2008-05-27
Officially this printer is not Supported as Canon does not provide Linux driver for iP1200 but there are work around available. they may or may not work, but at least you should try
[http://mynewbietips.blogspot.com/2007/06/installing-canon-pixma-ip1200-driver.html](http://mynewbietips.blogspot.com/2007/06/installing-canon-pixma-ip1200-driver.html)
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1200](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1200)


If you want sure shot sucess then use turboprint(paid)
[http://turboprint.info/](http://turboprint.info/)

---

### Post by phpmonkey on 2008-12-15
I agree with Gary4gar, I used the first link, but with a small modification, needing to use the cupsys admin to add teh printer:

I just got this working on my laptop using the following steps, from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Open up a terminal and 


1. ```
sudo nano /etc/apt/sources.list
```
Add the line > deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./ 

2. ```
sudo apt-get upgrade
```

3. ```
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

4. Open your web browser and go to > [http://127.0.0.1:631/](http://127.0.0.1:631/) which is the cupsys admin. Under the "home" tab" click "add printer" and follow the instructions, choosing > Canon iP2200 Ver.2.60 as your driver

5. Go to the "Printers" tab, and click "Print Test page".


It shoud be possible to do steps 4-5 through System>Administration>Printing but the correct driver wasn't showing up there for me, so I went through the cupsys browser admin instead.

Note: The only available printing option appears to be 600dpi

---

### Post by saralsasidharan on 2009-02-06
Hi all I am having Ubuntu 8.10 os my printer is canon pixma ip 1200 it's detected and shown in system >administration.printing but i'm unable to print any page . The printer is working fine in Xp. I wish to completely get rid of XP plese help

---

### Post by saralsasidharan on 2009-02-12
Hii this is not working for me the turbo print works

---


---
title: "Cannot print to Brother MFC240C on Lucid"
date: 2011-03-12
forum: Hardware
---

### Post by doesntcount on 2011-03-12
I'm having a hell of time printing and I'm hoping I could get some help.

I've installed the appropriate printer driver packages, as shown by my dpkg output below. 

And yet, when i print a testpage, it goes to the queue and enters the "Processing" stage and never actually prints.

I've added myself to the lp group, so it shouldn't be a permissions issue. 

It prints fine from my gf's mac, so there's nothing wrong with the printer. It's definitely a ubunut specific issue. Anybody have any suggestions? 

```
$ sudo dpkg -l | grep brother
[sudo] password for ****: 
ii  brother-cups-wrapper-bh7                        1.0.0-10-0ubuntu5                               Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common                     1.0.0-10-0ubuntu5                               Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                      1.2.1-0ubuntu3                                  Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-bh7                         1.0.1-1-0ubuntu3                                LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common                      1.0.0-4-0ubuntu1                                Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                       1.2.0-2-0ubuntu3                                LPR drivers for extra brother printers

```

---

### Post by doesntcount on 2011-03-12
Restarting the printer solved the issue. Go figure.

---

### Post by MyR on 2011-03-12
Hello there,

Glad you got your printer working!

I would be very grateful if you could take a couple minutes to explain [how you got the printer working]("http://linuxdeal.com/add-printer.php") on this site designed to help Linux users find printers!

Thank you in advance

---


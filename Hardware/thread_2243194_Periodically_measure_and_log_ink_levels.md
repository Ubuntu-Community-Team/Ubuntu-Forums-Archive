---
title: "Periodically measure and log ink levels"
date: 2014-09-07
forum: Hardware
---

### Post by Keith_Beef on 2014-09-07
So, here's an old, old problem.

I have an Epson Stylus Photo 890; it still works fine. Except that there's one problem with it that has been annoying me since I first bought it new, years ago.

When the ink levels get really low the printer no longer responds to the escputil command to query its ink levels. Now this printer has two ink cartridges: one for black and one for cyan, magenta and yellow. So if I don't regularly check the ink levels I can find myself in a situation where one of the two cartridges is just about empty, but I don't know which one since the printer won't respond to the query.

Imagine that the colour cartridge is empty.
[LIST=1]
[*]I replace the black cartridge.
[*]I query the levels.
[*]I get no response; this means that it was the colour cartridge that was empty.
[/LIST]
I have now opened and unsealed a black cartridge for noreason other than to query the levels.

So I started thinking that it would be nice to have ink levels logged somewhere periodically. This way if my printer stops working I can go and grep the logfile for the ink level and find the most recent measure. The mechanism should query the level and have a time out so that if the printer fails to respond for any reason (it may be switched off, or it may be refusing to respond because of low ink levels) the fact that the query timed out is logged. An alert should be logged if the printer responds with an ink level of below 10% remaining for any colour.

I've searched around and not found anything like this. Am I just looking in the wrong places? I can't believe that I'm the only person to have a problem like this.

---

### Post by yancek on 2014-09-07
I use an HP printer and it has something called "hp-toolbox".  Enter that in a terminal and it opens a GUI interface and has numerous options, one of which shows ink levels.  While you are waiting for a response here, you might try the Epson site to see if they have anything similar.  See if the link below helps as it specifically refers to Epson.

[http://ubuntuforums.org/showthread.php?t=2146656](http://ubuntuforums.org/showthread.php?t=2146656)

---

### Post by Vladlenin5000 on 2014-09-07
The Epson driver for your model should give the ink levels. It usually don't work in network installations but it should do its thing in locally (USB) installed printers.

---

### Post by tgalati4 on 2014-09-08
I only have HP printers, but a quick search of the repositories:

tgalati4@Mint14-Extensa ~ $ apt-cache search epson
epson-escpr - transitional dummy package for epson-escpr printer driver
escputil - maintenance utility for Epson Stylus printers
gle-graphics - Interactive Graphics Language Editor
libescpr-dev - printer driver for Epson Inkjet - library development files
libescpr1 - printer driver for Epson Inkjet - shared library
libimage-exiftool-perl - Library and program to read and write meta information in multimedia files
libinklevel-dev - development files for libinklevel5
libinklevel5 - library for checking the ink level of your local printer
[B]mtink - Status monitor tool for Epson inkjet printers
mtink-doc - Documentation for mtin[/B]k
photopc - Interface to digital still cameras
printer-driver-escpr - printer driver for Epson Inkjet that use ESC/P-R

If you can find a query tool for the commandline, then you can run a cronjob to check it once a day and dump that to a log file.

```
crontab -e
```

---

### Post by coffeecat on 2014-09-08
Posted in Multimedia forum.

*Thread moved to **Hardware**.*

---

### Post by christopher9 on 2014-09-08
Have you tried mtink in Software Center ?

---


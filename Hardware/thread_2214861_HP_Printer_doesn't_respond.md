---
title: "HP Printer doesn't respond"
date: 2014-04-03
forum: Hardware
---

### Post by mark allyn on 2014-04-03
Hello everyone,

Until yesterday morning my HP p1505 laser jet printer worked marvelously well.  I had run a couple of print jobs the day before without a problem.  Whilst consuming a piece of toast I heard the printer spontanoeously print the jobs it had run the previous day.  Strange behavior indeed.  After that I tried to run a couple of other jobs and the printer simply would not respond at all.  It will run a test page, but it doesn't appear to know anything about my system.  I have turned the machine off and on.  I also have restarted my computer.  No dice.  BTW. I am running 12.04.  

It appears there is something wrong with the driver.  But, I haven't a clue as to how to go about troubleshooting and repairing it.

Any suggestions are most welcome.

Regards,
Mark Allyn

---

### Post by oldfred on 2014-04-03
Was it jam or jelly on toast? That may have been the problem? :)

Are you using hplip from repository for the verison directly from HP?
I got a newer HP printer and with 12.04 the verison in repository was very old, so I downloaded hplip directly from HP.

HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

With the version I have, I can open an HP gui to look at and maintain printer. Not sure if then you also have cups or not. I am not at computer with HP printer so I cannot test.

In Firefox I have used this with my other printer.
[http://localhost:631/printers](http://localhost:631/printers)

---

### Post by mark allyn on 2014-04-03
Hi OldFred,

Thanks for the help on this issue.  I honestly don't know how I got the printer initially hooked up to 12.04.  Originally I had used it with a Microsoft OS.  It sat idle for awhile when I switched over to 12.04.  Then somehow I stumbled upon something called SAMBA and/or CUPS.  Don't remember how.  But, anyway it started to work fine and did so for many months.  

I'll try downloading from HP, unless my mumbling about SAMBA/CUPs rings a bell.

The jelly, incidentally, was a private label currant jelly.  Quite tasty on lo-carb brown bread.

Thanks,
Mark

---

### Post by mark allyn on 2014-04-03
Hi OldFred,

I did as you suggested and downloaded from the HP site.  Installation went smoothly.  The printer now functions.  I can return to my currant jelly and brown bread.  Not a moment too soon.

Many thanks,
Mark Allyn

---

### Post by oldfred on 2014-04-03
Glad you got it working.

I never liked current jelly. But brings back good memories as Mom made it from our own currents. But I prefered the grape jelly as we also had a grape arbor. May have to go back and try it again, it must have been 60 years ago.

---


---
title: "Canon MX700 Printer Problems"
date: 2009-08-21
forum: Hardware
---

### Post by ThomasTheTan on 2009-08-21
Hi,

I'm trying to get this printer to work.  I followed the steps found in [this]("http://ubuntuforums.org/showthread.php?t=571795") thread (the last page provides a synopsis).  That is,

I installed both the canon common driver and the mp520 driver then added the printer with the specified ppd file (all three files are found [here]("http://ubuntuforums.org/showthread.php?t=571795&page=9")).  

Every time that I try to print anything, however, nothing prints and I get the message that /usr/lib/cups/filter/pstocanonij failed.

To try to fix this, I uninstalled both drivers and reinstalled them, making sure to restart CUPS after each installation.  This didn't change anything.  Additionally, I tried editing the ppd file slightly so that the line that originally said

*cupsFilter: "application/vnd.cups-postscript 0 pstocanonij"

Now says

*cupsFilter: "application/vnd.cups-postscript 0 /usr/lib/cups/filter/uspstocanonij"

This also didn't change anything.

The CUPS error log produces this message every time I try to print something:

"PID **** (/usr/lib/cups/filter/pstocanonij) stopped with status 22!"

So clearly that file isn't working (it does exist, and is in both /usr/lib/cups/filter and /usr/lib64/cups/filter).  Anyone have any ideas about how to fix it?

Thanks.

---

### Post by A_teen_Geek on 2009-10-17
i had the same problem and through lots of research (and hair pulling) i found the solution and i wrote this([http://ubuntuforums.org/showthread.php?t=1227295&highlight=mx700](http://ubuntuforums.org/showthread.php?t=1227295&highlight=mx700)) to gather all the info i found just follow the instructions and links
if you have any programs contact me:guitar:

---


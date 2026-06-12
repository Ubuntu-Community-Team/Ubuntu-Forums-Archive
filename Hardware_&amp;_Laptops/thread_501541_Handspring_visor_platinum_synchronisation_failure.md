---
title: "Handspring visor platinum synchronisation failure"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by kenmonk on 2007-07-15
I have this old PDA which I still use for addresses, memos, etc.  I have managed to get it to synchronise with earlier versions of Linux, certainly with an earlier Mandrake.  Feisty seems to be giving problems, though, and the number of posts on the subject suggest that this is a constant problem.

I've found the "Palm Device Setup" article and done all that says to no avail.  I can't get either jpilot or kpilot to see the machine properly.  They both seem to know that something is there (sometimes, anyway), but fail to talk to it.

In desperation I turned to the command line tool "pilot-xfer".  With this I managed to do a backup and a sync, but only with a reboot between them.  It would seem that, having made one connection to "/dev/ttyUSB2" no more are possible.  I tried removing the visor module with "modprobe -r visor" and then put it back again, but the results are the same - no port is available.

The exact message is:
    Unable to bind to port: /dev/ttyUSB1
   Please use --help for more information
which is strange when this has just worked!!

Has anyone any suggestion before I pull the last of my hair out??!!

                 Ken.

---


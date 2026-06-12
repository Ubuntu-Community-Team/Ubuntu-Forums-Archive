---
title: "Printing Problems with Dapper Drake"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Jester A. on 2006-07-12
well. this is my first post.  I've spent about 5 hours combing different bulletin boards trying to figure out how to get my printer working, but i have had no luck so far...

Does anyone know of a comprehensive, step-by-step way of troubleshooting a printer in Ubuntu?

I've installed it with Gnome Menu: System --> Administration --> Printing utility and then verified it all with the cups browser interface ([http://localhost:631/printers/)](http://localhost:631/printers/)).  And it always seems like there's something wrong with my parallel port.

From the CUPS browser interface, i get the "Parallel port busy; will retry in 30 seconds..." message.

But from the xterm when I use the lpq command, it seems like its just sitting: 

BJC-210 is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  guest   24      Test Page                       18432 bytes

I don't know what to do.  5 hours is too long...

My printer is a Canon BJC-210.

Any solutions would be most appreciated...

-- jester a.

---

### Post by tonderai on 2006-07-22
Same problem here with a Canon i865. Sits there fine and "ready" until you go to print, then gives "Paused: Unable to open parallel port device file "": No such file or directory".

Any ideas appreciated.

---

### Post by Ron Byers on 2006-07-26
I have the exact same problem with a Canon BJC-3000. Is this a bug?

---

### Post by tonderai on 2006-07-27
> **tonderai said:**
> Same problem here with a Canon i865. Sits there fine and "ready" until you go to print, then gives "Paused: Unable to open parallel port device file "": No such file or directory".

Any ideas appreciated.

I have also tested the i865 using a USB connection, a similar thing happens. So it seems its nothing to do with the parallel port specifically.

I'm also not sure what troubleshooting steps to take.

---

### Post by felippe miranda on 2006-08-11
try to install it with Gnome Menu: System --> Administration --> Printing utility , with power down in the printer. Select port ====> LPT #1. Next box ======> select CANON and the specific driver of your printer BJC 250 . Do not comment any of the spaces in the next box ======> apply.
It worked for my CANON bjc-4300 with DAPPER .

---

### Post by wpshooter on 2006-08-11
I have this same problem with my HP laserjet 2100 which I have hooked locally to lpt1 of one Ubuntu computer BUT I can not print to it from one of my other Ubuntu computers.  This is attempted using the CUPS localhost:631 interface.

I just do not believe that they have the printing side of this O/S down pat yet.  I have just about given up on getting this to work.  If most people that were trying to get a printer setup on a M/S windows system had this much problem getting a simple print sharing to work, they would tell M/S to go jump in a lake !!!

This should be just a matter of a few simple clicks and placing a few parameters in a GUI interface, but NOT.

---

### Post by tillsch on 2006-09-07
Hello, I want to report that i have the same problem with a Canon i550 and don't know how to proceed. It seems so that mainly Canon printers are affected. I think I'll have a try in a Debian forum, maybe they could help.

Here is a part of my error_log (var/log/cups):
E [07/Sep/2006:15:25:41 +0200] cupsdAuthorize: Local authentication certificate not found!
E [07/Sep/2006:15:25:43 +0200] PID 7419 (/usr/lib/cups/backend/canon_parallel) stopped with status 1!
E [07/Sep/2006:15:25:43 +0200] [Job 16] No %%BoundingBox: comment in header!
E [07/Sep/2006:15:25:43 +0200] [Job 16] Unable to open parallel port device file "": No such file or directory
E [07/Sep/2006:15:25:46 +0200] cupsdAuthorize: Local authentication certificate not found!
...
E [07/Sep/2006:15:25:51 +0200] cupsdAuthorize: Local authentication certificate not found!
E [07/Sep/2006:15:25:55 +0200] PID 7418 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
E [07/Sep/2006:15:25:56 +0200] cupsdAuthorize: Local authentication certificate not found!

regard, till

---

### Post by tillsch on 2006-09-07
I think I have it, my printer works.:-D 

You have to go in the printer settings --> connection. There you choose a printer by indicating the port "LPT #1" (no other!). Now the error shouldn't occur anymore.

---


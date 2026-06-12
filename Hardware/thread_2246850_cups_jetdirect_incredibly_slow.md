---
title: "cups jetdirect incredibly slow"
date: 2014-10-03
forum: Hardware
---

### Post by ghelbig on 2014-10-03
Printing with cups to a jetdirect is incredibly slow - a web page typically takes 6-8 hours to render.  With Chrome it will chug along for many hours, error out, then go to the next page, chug along for many hours, error out, then go to the next page, chug along for many hours...

Some pages come out 4~5 days after the print request.

I do not have this problem with non-cups printers.  Non-linux machines work "just fine".  FireFox on non-ubuntu seems "OK".  With Chrome on ubuntu, well, the glaciers are melting faster.

The only other clue is that (now) with Open Office the page gets to the printer then gets the printer wedged.  Pressing the 'clear error' on the printer gets a properly-printed page to eject.

The cups printers are genuine HP (2200 and 5000) with the latest and greatest JetDirect code and printer firmware.

Any tips/hints/clues?  IIRC it was working "last year", and it was a couple of updates ago that it died (I don't print a lot - trying to save trees)

Thanks!

---

### Post by tgalati4 on 2014-10-03
Check for errors in /var/log/cups.  It could be hardware problems.  Older HP printers develop all sorts of problems, including processor problems that cause delays.  Try cleaning them and reseating the RAM in the printers.  Also reseat the network cables on both ends (at the printer and at the switch).

---

### Post by ghelbig on 2014-10-30
This is the only error in /var/log/cups/error_log:
E [30/Oct/2014:14:30:56 -0700] [Job 807] Stopping unresponsive job!

That was from trying to print a test page while another job was stuck at "processing - not connected".

I doubt that it's a hardware problem - Windows and CentOS have no trouble printing to it.

While I'm at it - the 'move to another queue' command is a null-op.

And I searched these forums - similar problems have bee happening since 2009, and all of the threads I found just end w/o resolution.

Gary.

---

### Post by tgalati4 on 2014-10-30
Delete the printer from within CUPS and reinstall within CUPS.  Sometimes the printer queue gets balled up.  Typically after a minor kernel update.

---


---
title: "Ricoh Aficio MP 1600 driver on 12.04"
date: 2012-07-27
forum: Hardware
---

### Post by firstbishop on 2012-07-27
I've been battling this for weeks and would appreciate a fresh pair of eyes:

I have a multifunction copier / printer (Ricoh Aficio MP1600) that is connected via USB to a Win XP machine on our network. The XP machine also has a little HP LaserJet connected to it, also by USB. The XP machine prints fine to both printers.

Using CUPS I can print to the HP without any problems from my Ubuntu machine, but have not been able to set up the Ricoh (whether over the network, or with the printer plugged directly into the Linux box). I have tried official Postscript and PXL drivers, all sorts of generic options - foomatic, gutenprint, raw queue, text only. Using IPP, HTTP, Samba, etc. 

From the CUPS side it looks like the print job is going through fine - the logs show the job being printed successfully. But nothing comes out of the printer. When using foomatic-rip the foomatic-rip ps files in the tmp directory are all empty (0KB).

There seem to be numbers of posts in these forums and others where people talk about CUPS mistakenly reporting successful printing, but nothing I've tried has helped. Any other ideas?

Thanks

Michael

---

### Post by firstbishop on 2012-07-27
Now I've managed to produce some foomatic tmp ps files that contain content. Tried printing using one of these /usr/bin/lpr as root. The job shows up as completed in the CUPS log, but nothing happens on the printer.

---


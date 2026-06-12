---
title: "Clearing/limiting size of syslog to debug wifi?"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by bushwacker on 2007-06-10
Hi, I have a new Linksys PCMCIA card using ndiswrapper that is mysteriously crapping out all the time as of a couple of days ago. I want to post the error messages about it in order to get some feedback here, but I can't open my syslog. It must be something close to 1GB in size, because trying to read it in the GUI viewer or via a text program hogs all the memory and nearly locks up the system. Is there an easy command (tail perhaps?) that will allow me to just cut off everything but the last few MB of log entries, then limit the log file size to say 20MB? 

Muchas gracias.

---

### Post by 444 on 2007-06-10
tail -c howmanybytes logfile > shortenedlogfile
from 'man tail' btw.

---


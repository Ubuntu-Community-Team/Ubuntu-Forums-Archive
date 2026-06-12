---
title: "IOGear GPSU21 Print Server error with 12.04"
date: 2013-07-19
forum: Hardware
---

### Post by BarryTice on 2013-07-19
Greetings, all.

I have Ubuntu 12.04 running, and have been printing to a shared Canon D480 hanging off an old Windows XP box on my network without issue. But that old box has started to fail, so I acquired an IOGear GPSU21 Print Server, and am trying to get it configured.

When I attempt to print to it, I get the following status in my Printer State:
Processing - Error writing spool: NT_STATUS_IO_TIMEOUT

I have followed Poser55's instructions given here in [http://ubuntuforums.org/showthread.php?t=1658955](http://ubuntuforums.org/showthread.php?t=1658955), adding "Allow all" entries to my /etc/cups/cupsd.conf file, but it has not helped.

I have not added the "Port 631" entry specified, as my cupsd.con file already contained a "Listen localhost:631" entry immediately before the "Listen /var/run/cups/cups.sock" entry.

I have rebooted my system after making my cupsd.conf changes, but that has not helped any.

I would welcome any assistance or relevent advice. Thank you for your efforts!

-- Barry

---


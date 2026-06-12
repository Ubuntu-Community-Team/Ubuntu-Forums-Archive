---
title: "canon pixma does not print"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by ouphe on 2005-09-19
I've installed the Canon Pixma ip4000 printer as described in:
[http://ubuntuforums.org/archive/index.php/t-38995.html](http://ubuntuforums.org/archive/index.php/t-38995.html) 

The setup went fine, no errors at all. But ultimately the printer does not print.
I can't find any clues in the cups error log:

I [19/Sep/2005:16:54:24 +0200] Adding start banner page "none" to job 12.
I [19/Sep/2005:16:54:24 +0200] Adding end banner page "none" to job 12.
I [19/Sep/2005:16:54:24 +0200] Job 12 queued on 'PIXUS-iP4100-Ver.2.50' by 'bas'.
I [19/Sep/2005:16:54:24 +0200] Started filter /usr/lib/cups/filter/pstops (PID 9725) for job 12.
I [19/Sep/2005:16:54:24 +0200] Started filter /usr/lib/cups/filter/pstocanonbj (PID 9726) for job 12.
I [19/Sep/2005:16:54:24 +0200] Started backend /usr/lib/cups/backend/usb (PID 9727) for job 12.
I [19/Sep/2005:16:54:36 +0200] Printer 'PIXUS-iP4100-Ver.2.50' deleted by 'root'.
I [19/Sep/2005:16:54:36 +0200] Saving printers.conf...


Changing printer settings, paper source, etc does not change anything. Anybody have an idea?

---


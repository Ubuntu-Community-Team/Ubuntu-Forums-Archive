---
title: "cupsdAuthorize: No authentication data provided."
date: 2008-04-30
forum: Hardware
---

### Post by sphilli8 on 2008-04-30
I have had printer problems ever since I switched from XP to Windows nearly a year ago, but not as bad as since I upgraded to Hardy last week....

The printer is a Fuji-Xerox c525a networked printer. I downloaded the driver from the FX website as an rpm, converted it to deb with Alien, and installed it.

When I try and print, the job just gets held. Occasionally it will get through if I'm only printing a page, but mostly that doesn't even work. I have pasted some of the CUPS error log below, with the important bits in red.

Any ideas?

> D [01/May/2008:21:45:47 +1000] [Job 13] Read 8192 bytes of print data...
D [01/May/2008:21:45:47 +1000] Discarding unused printer-state-changed event...
D [01/May/2008:21:45:47 +1000] cupsdAcceptClient: 7 from localhost (Domain)
D [01/May/2008:21:45:47 +1000] cupsdReadClient: 7 POST / HTTP/1.1
D [01/May/2008:21:45:47 +1000] cupsdAuthorize: No authentication data provided.
D [01/May/2008:21:45:47 +1000] Get-Jobs ipp://localhost/jobs/
D [01/May/2008:21:45:47 +1000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/May/2008:21:45:47 +1000] cupsdReadClient: 7 POST / HTTP/1.1
D [01/May/2008:21:45:47 +1000] cupsdAuthorize: No authentication data provided.
D [01/May/2008:21:45:47 +1000] CUPS-Get-Printers
D [01/May/2008:21:45:47 +1000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/May/2008:21:45:47 +1000] cupsdCloseClient: 7
D [01/May/2008:21:45:47 +1000] Discarding unused printer-state-changed event...
D [01/May/2008:21:45:47 +1000] Discarding unused printer-state-changed event...
D [01/May/2008:21:45:47 +1000] [Job 13] Wrote 8192 bytes of print data...
D [01/May/2008:21:45:47 +1000] [Job 13] Read 8192 bytes of print data...
[COLOR="Red"]**E [01/May/2008:21:45:47 +1000] [Job 13] Unable to write print data: Broken pipe**[/COLOR]
D [01/May/2008:21:45:47 +1000] Discarding unused printer-state-changed event...
D [01/May/2008:21:45:47 +1000] PID 14348 (/usr/lib/cups/filter/FXM_PF) exited with no errors.
[COLOR="Red"]**E [01/May/2008:21:45:47 +1000] PID 14349 (/usr/lib/cups/backend/socket) stopped with status 1!**[/COLOR]
D [01/May/2008:21:45:47 +1000] [Job 13] File 0 is complete.
I [01/May/2008:21:45:47 +1000] [Job 13] Backend returned status 1 (failed)
D [01/May/2008:21:45:47 +1000] Discarding unused printer-state-changed event...
[COLOR="Red"]**E [01/May/2008:21:45:47 +1000] [Job 13] Canceling job since it could not be sent after 5 tries.**[/COLOR]
D [01/May/2008:21:45:47 +1000] Discarding unused job-completed event...
D [01/May/2008:21:45:48 +1000] [Job 13] Unloading...
D [01/May/2008:21:45:59 +1000] Report: clients=0
D [01/May/2008:21:45:59 +1000] Report: jobs=14
D [01/May/2008:21:45:59 +1000] Report: jobs-active=1
D [01/May/2008:21:45:59 +1000] Report: printers=2
D [01/May/2008:21:45:59 +1000] Report: printers-implicit=0
D [01/May/2008:21:45:59 +1000] Report: stringpool-string-count=618
D [01/May/2008:21:45:59 +1000] Report: stringpool-alloc-bytes=9648
D [01/May/2008:21:45:59 +1000] Report: stringpool-total-bytes=12440
D [01/May/2008:21:46:30 +1000] cupsdAcceptClient: 7 from localhost (Domain)
D [01/May/2008:21:46:30 +1000] cupsdReadClient: 7 POST / HTTP/1.1
D [01/May/2008:21:46:30 +1000] cupsdAuthorize: No authentication data provided.
D [01/May/2008:21:46:30 +1000] CUPS-Get-Printers
D [01/May/2008:21:46:30 +1000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/May/2008:21:46:30 +1000] cupsdCloseClient: 7
D [01/May/2008:21:47:04 +1000] Report: clients=0
D [01/May/2008:21:47:04 +1000] Report: jobs=14
D [01/May/2008:21:47:04 +1000] Report: jobs-active=1
D [01/May/2008:21:47:04 +1000] Report: printers=2
D [01/May/2008:21:47:04 +1000] Report: printers-implicit=0
D [01/May/2008:21:47:04 +1000] Report: stringpool-string-count=618
D [01/May/2008:21:47:04 +1000] Report: stringpool-alloc-bytes=9648
D [01/May/2008:21:47:04 +1000] Report: stringpool-total-bytes=12440


---

### Post by sphilli8 on 2008-05-02
I found a solution!
See it here:
[http://ubuntuforums.org/showthread.php?t=483415](http://ubuntuforums.org/showthread.php?t=483415)

As the old saying goes: when in doubt, consult the manual. The problem appears to be that I added the printer using the KDE Add Printer Wizard. It was automatically given a "socket" URI instead of an "lpd" one. When I:
 - altered the printer settings at [http://localhost:631](http://localhost:631) (the CUPS admin page) as instructed in the manual for the printer, and
 - copied the PPD file into a second place on the hard drive (as instructed on ubunutuforums, see the link above)

..everything started working.

It's still slower than windows, but I can live with that.

---

### Post by grantbuntu on 2008-11-24
I found that the only thing I needed to do was change socket to lpd (and remove :9100 off the end as well).  See [ Solving Ubuntu printer “broken pipe” problem (DocuPrint C525A) ]("http://p-s.co.nz/wordpress/?p=227").  BTW thanks for steering me in the right direction - very grateful.

---


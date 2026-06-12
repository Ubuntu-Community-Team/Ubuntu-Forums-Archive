---
title: "I've inherited an ancient printer..."
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by Fyrehardt on 2007-07-30
And even though the OpenPrinting data base says it should work perfectly, I'm starting to think it's a paperweight.

It's an Okidata 810e.  It seems to get the printing jobs, but it won't do the printing jobs.  The printer menu properties says "Printing: No %%BoundingBox: comment in header!".  I followed instructions elsewhere on the web and reset the cups error log to debug, and have looked at it.  Here's a sample of it.  It just sits there and loops.

```
D [30/Jul/2007:01:34:33 -0400] CUPS-Get-Printers
D [30/Jul/2007:01:34:33 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:33 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:33 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:33 -0400] Get-Printer-Attributes ipp://localhost/printers/OL810ex
D [30/Jul/2007:01:34:33 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:34 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:34 -0400] CUPS-Get-Printers
D [30/Jul/2007:01:34:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:34 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:34 -0400] Get-Printer-Attributes ipp://localhost/printers/OL810ex
D [30/Jul/2007:01:34:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:34 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:34 -0400] Get-Jobs ipp://localhost:631/printers/OL810ex
D [30/Jul/2007:01:34:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:37 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [30/Jul/2007:01:34:37 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:37 -0400] CUPS-Get-Printers
D [30/Jul/2007:01:34:37 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:37 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [30/Jul/2007:01:34:37 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:37 -0400] Get-Printer-Attributes ipp://localhost/printers/OL810ex
D [30/Jul/2007:01:34:37 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:37 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:37 -0400] Get-Jobs ipp://localhost:631/printers/OL810ex
D [30/Jul/2007:01:34:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:38 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:38 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:38 -0400] CUPS-Get-Printers
D [30/Jul/2007:01:34:38 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:38 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:38 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:38 -0400] Get-Printer-Attributes ipp://localhost/printers/OL810ex
D [30/Jul/2007:01:34:38 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:40 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:40 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:40 -0400] CUPS-Get-Printers
D [30/Jul/2007:01:34:40 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:40 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:40 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:40 -0400] Get-Printer-Attributes ipp://localhost/printers/OL810ex
D [30/Jul/2007:01:34:40 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:40 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:40 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:40 -0400] Get-Jobs ipp://localhost:631/printers/OL810ex
D [30/Jul/2007:01:34:40 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:42 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [30/Jul/2007:01:34:42 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:42 -0400] CUPS-Get-Printers
D [30/Jul/2007:01:34:42 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:42 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [30/Jul/2007:01:34:42 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:42 -0400] Get-Printer-Attributes ipp://localhost/printers/OL810ex
D [30/Jul/2007:01:34:42 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:42 -0400] cupsdReadClient: 7 POST /jobs HTTP/1.1
D [30/Jul/2007:01:34:42 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:42 -0400] Cancel-Job ipp://localhost/jobs/19
D [30/Jul/2007:01:34:42 -0400] Discarding unused job-completed event...
I [30/Jul/2007:01:34:42 -0400] Job 19 was canceled by "faeya".
D [30/Jul/2007:01:34:42 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:42 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:42 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:42 -0400] Get-Jobs ipp://localhost:631/printers/OL810ex
D [30/Jul/2007:01:34:42 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:43 -0400] Unloading job 19...
D [30/Jul/2007:01:34:43 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:43 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:43 -0400] Get-Jobs ipp://localhost:631/printers/OL810ex
D [30/Jul/2007:01:34:43 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:44 -0400] cupsdReadClient: 7 POST /jobs HTTP/1.1
D [30/Jul/2007:01:34:44 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:44 -0400] Cancel-Job ipp://localhost/jobs/18
D [30/Jul/2007:01:34:44 -0400] Discarding unused job-completed event...
I [30/Jul/2007:01:34:44 -0400] Job 18 was canceled by "faeya".
D [30/Jul/2007:01:34:44 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [30/Jul/2007:01:34:44 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [30/Jul/2007:01:34:44 -0400] cupsdAuthorize: No authentication data provided.
D [30/Jul/2007:01:34:44 -0400] Get-Jobs ipp://localhost:631/printers/OL810ex
```

Please, if anyone can help me out here, I'll mail them chocolate chip cookies or something!  I'll do *anything* to not have to hook the printer to my boyfriend's XP machine.  I'm going to be the one using it the most...*cries*

---

### Post by ronny_d on 2007-07-30
Hi, it is, i suppose, not the paperweight. I had the same problem "boundingsbox" nonsense and "cannot find host parallel port" or something maybe could come next? Maybe not..., but i don't know about CUPS and that is why i started a new post just before i read yours:

 [http://ubuntuforums.org/showthread.php?t=513077](http://ubuntuforums.org/showthread.php?t=513077)

I ask for good (!) experiences, by the way. 


I mean: i read so many bad experiences with CUPS and printer connection on this forum... that i started to suspect... and this suspicion fed because i am no drilled geek computertechnician and i just only want to print and not being fooled because i may know too little and being sent from wall to wall without result and i concluded my parallel port would be broken or some wrong in the bios..., but why so many others have problems with configuring with CUPS? So i opened up the new thread and hope to receive loads of good experiences however... and i hope it was i who did something wrong in CUPS... So i am waiting for positive replies on my thread.

---


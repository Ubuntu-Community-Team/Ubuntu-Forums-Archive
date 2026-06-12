---
title: "LPR Printing not working after Natty Upgrade"
date: 2011-08-14
forum: Hardware
---

### Post by gcave on 2011-08-14
Ever since I upgraded to Natty, I have been unable to print.  In fact, my printer setting were completely missing and I had to reinstall my LPR printer.  The job never makes it to my print server.  I can telnet to the print server on TCP 515, it not an IP connectivity issue.  When I looked at the log file I get:

D [14/Aug/2011:14:19:47 -0500] [Job 7] STATE: +connecting-to-device
D [14/Aug/2011:14:19:47 -0500] [Job 7] Looking up "192.168.1.222"...
D [14/Aug/2011:14:19:47 -0500] [Job 7] Connecting to 192.168.1.222:515 for printer l1prn1
D [14/Aug/2011:14:19:47 -0500] [Job 7] Connecting to printer...
D [14/Aug/2011:14:19:47 -0500] [Job 7] STATE: -connecting-to-device
D [14/Aug/2011:14:19:47 -0500] [Job 7] Connected to printer...
D [14/Aug/2011:14:19:47 -0500] [Job 7] Connected to 192.168.1.222:515 (IPv4) (local port 1023)...
D [14/Aug/2011:14:19:47 -0500] [Job 7] lpd_command 02 l1prn1
D [14/Aug///2011:14:19:47 -0500] [Job 7] Sending command string (8 bytes)...
D [14/Aug/2011:14:19:47 -0500] [Job 7] Reading command status...
D [14/Aug/2011:14:19:47 -0500] [Job 7] lpd_command returning 32
D [14/Aug/2011:14:19:47 -0500] [Job 7] Backend returned status 1 (failed)
D [14/Aug/2011:14:19:47 -0500] [Job 7] End of messages
D [14/Aug/2011:14:19:47 -0500] [Job 7] printer-state=3(idle)
D [14/Aug/2011:14:19:47 -0500] [Job 7] printer-state-message="/usr/lib/cups/backend/lpd failed"
D [14/Aug/2011:14:19:47 -0500] [Job 7] printer-state-reasons=none

Any advise?

---


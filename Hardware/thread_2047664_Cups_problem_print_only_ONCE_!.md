---
title: "Cups problem/ print only ONCE !"
date: 2012-08-25
forum: Hardware
---

### Post by dargaud on 2012-08-25
Hello all,
a recent upgrade broke something in CUPS. For the last few months I on one of my systems I can print only ONCE. Any subsequent print stays in the job queue with the printer blinking that it's receiving data.

Cups says:
Epson_Stylus_Office_B42WD-689 / Withheld / 87k / printing since Sat Aug 25 17:33:12 2012 "Processing page 1..."
But nothing comes out.
 

Here's a cups debug dump of the first print and the next attempt:
```
D [25/Aug/2012:17:32:34 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:34 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [25/Aug/2012:17:32:34 +0200] CUPS-Get-Default
D [25/Aug/2012:17:32:34 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:34 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [25/Aug/2012:17:32:34 +0200] CUPS-Get-Default
D [25/Aug/2012:17:32:34 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:34 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:34 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:34 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 18 GET /printers/Epson_Stylus_Office_B42WD.ppd HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:34 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:34 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:34 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:34 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:34 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:34 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:34 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:35 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:35 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:35 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:35 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:35 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:35 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:35 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:35 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:35 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:35 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:35 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:35 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:35 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:35 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:36 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:36 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:36 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:36 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:36 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:36 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:36 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:36 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:36 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:37 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:37 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:37 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:37 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:37 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:37 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:37 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:32:37 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:32:37 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:32:37 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:32:37 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:32:37 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:32:38 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:32:38 +0200] cupsdReadClient: 17 POST /printers/Epson_Stylus_Office_B42WD HTTP/1.1
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:32:38 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:32:38 +0200] cupsdReadClient: 17 1.1 Print-Job 1
D [25/Aug/2012:17:32:38 +0200] Print-Job ipp://localhost:631/printers/Epson_Stylus_Office_B42WD
D [25/Aug/2012:17:32:38 +0200] [Job ???] Auto-typing file...
I [25/Aug/2012:17:32:38 +0200] [Job ???] Request file type is application/pdf.
D [25/Aug/2012:17:32:38 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"
D [25/Aug/2012:17:32:38 +0200] add_job: requesting-user-name="alain"
I [25/Aug/2012:17:32:38 +0200] [Job 688] Adding start banner page "none".
D [25/Aug/2012:17:32:38 +0200] Discarding unused job-created event...
D [25/Aug/2012:17:32:38 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [25/Aug/2012:17:32:38 +0200] [Job 688] Adding end banner page "none".
I [25/Aug/2012:17:32:38 +0200] [Job 688] File of type application/pdf queued by "alain".
D [25/Aug/2012:17:32:38 +0200] [Job 688] hold_until=0
I [25/Aug/2012:17:32:38 +0200] [Job 688] Queued on "Epson_Stylus_Office_B42WD" by "alain".
D [25/Aug/2012:17:32:38 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [25/Aug/2012:17:32:38 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:38 +0200] [Job 688] job-sheets=none,none
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[0]="Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[1]="688"
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[2]="alain"
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[3]="Tâches - CUPS 1.5.3"
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[4]="1"
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[5]="Rotate180=Off DensityWatermark=Level4 SizeWatermark=70 BrightnessValue=0 PrintQuality=Text number-up=1 Watermark=None YellowValue=0 PageSize=Letter ReduceEnlarge=Off OutputPaper=A4 MirrorImage=Off CyanValue=0 PositionWatermark=Center PosterPrinting=Off GammaValue=2.2 ScaleRatio=100 AdjustPrintDensity=TextPhoto Color=Grayscale Duplex=DuplexNoTumble MediaType=PLAIN ColurWatermark=Red ContrastValue=0 MagentaValue=0 SaturationValue=0 CorrectionColor=EPSONVivid FaceDown=Off Borderless=Off job-uuid=urn:uuid:b8d8bc62-373e-3845-4279-4f4c80dbd0c2 job-originating-host-name=localhost time-at-creation=1345908758 time-at-processing=1345908758"
D [25/Aug/2012:17:32:38 +0200] [Job 688] argv[6]="/var/spool/cups/d00688-001"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[8]="HOME=/var/spool/cups/tmp"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[10]="SERVER_ADMIN=root@alain-desktop"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[11]="SOFTWARE=CUPS/1.5.3"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[13]="USER=root"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[16]="IPP_PORT=631"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[17]="CHARSET=utf-8"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[18]="LANG=fr_FR.UTF-8"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[19]="PPD=/etc/cups/ppd/Epson_Stylus_Office_B42WD.ppd"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[20]="RIP_MAX_CACHE=128m"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[21]="CONTENT_TYPE=application/pdf"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[22]="DEVICE_URI=usb://EPSON/Stylus%20Office%20B42WD?serial=4D4734593031313566"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[23]="PRINTER_INFO=Epson Stylus Office B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[24]="PRINTER_LOCATION="
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[25]="PRINTER=Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[26]="PRINTER_STATE_REASONS=none"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[27]="CUPS_FILETYPE=document"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[28]="FINAL_CONTENT_TYPE=printer/Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[29]="AUTH_I****"
I [25/Aug/2012:17:32:38 +0200] [Job 688] Started filter /usr/lib/cups/filter/pdftopdf (PID 2454)
I [25/Aug/2012:17:32:38 +0200] [Job 688] Started filter /usr/lib/cups/filter/gstoraster (PID 2455)
I [25/Aug/2012:17:32:38 +0200] [Job 688] Started filter /opt/epson-inkjet-printer-workforce-635-nx625-series/cups/lib/filter/epson_inkjet_printer_filter (PID 2456)
I [25/Aug/2012:17:32:38 +0200] [Job 688] Started backend /usr/lib/cups/backend/usb (PID 2457)
D [25/Aug/2012:17:32:38 +0200] Discarding unused job-state-changed event...
D [25/Aug/2012:17:32:38 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/Epson_Stylus_Office_B42WD) from localhost
D [25/Aug/2012:17:32:38 +0200] [Job 688] libusb_get_device_list=6
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients and dirty files"
D [25/Aug/2012:17:32:38 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:32:38 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:32:38 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [25/Aug/2012:17:32:38 +0200] [Job 688] STATE: +connecting-to-device
D [25/Aug/2012:17:32:38 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:38 +0200] [Job 688] STATE: -connecting-to-device
D [25/Aug/2012:17:32:38 +0200] Discarding unused printer-state-changed event...
I [25/Aug/2012:17:32:38 +0200] [Job 688] Sending data to printer.
D [25/Aug/2012:17:32:38 +0200] [Job 688] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [25/Aug/2012:17:32:38 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:32:38 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:38 +0200] [Job 688] PPD uses qualifier 'RGB.PLAIN.'
D [25/Aug/2012:17:32:38 +0200] [Job 688] Calling FindDeviceById(Epson_Stylus_Office_B42WD)
D [25/Aug/2012:17:32:38 +0200] [Job 688] Failed to send: org.freedesktop.ColorManager.Failed:device id 'Epson_Stylus_Office_B42WD' does not exists
D [25/Aug/2012:17:32:38 +0200] [Job 688] Failed to get profile filename!
I [25/Aug/2012:17:32:38 +0200] [Job 688] no profiles specified in PPD
D [25/Aug/2012:17:32:38 +0200] [Job 688] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [25/Aug/2012:17:32:38 +0200] [Job 688] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -r360x360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=0 -dcupsCompression=1 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c -f -_
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[8]="HOME=/var/spool/cups/tmp"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[10]="SERVER_ADMIN=root@alain-desktop"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[11]="SOFTWARE=CUPS/1.5.3"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[12]="USER=root"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[15]="IPP_PORT=631"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[16]="CHARSET=utf-8"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[17]="LANG=fr_FR.UTF-8"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[18]="PPD=/etc/cups/ppd/Epson_Stylus_Office_B42WD.ppd"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[19]="RIP_MAX_CACHE=128m"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[20]="CONTENT_TYPE=application/pdf"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[21]="DEVICE_URI=usb://EPSON/Stylus%20Office%20B42WD?serial=4D4734593031313566"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[22]="PRINTER_INFO=Epson Stylus Office B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[23]="PRINTER_LOCATION="
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[24]="PRINTER=Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[25]="PRINTER_STATE_REASONS=none"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[26]="CUPS_FILETYPE=document"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[27]="FINAL_CONTENT_TYPE=printer/Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:32:38 +0200] [Job 688] envp[28]="AUTH_INFO_REQUIRED=none"
D [25/Aug/2012:17:32:38 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:32:38 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:38 +0200] PID 2454 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
I [25/Aug/2012:17:32:38 +0200] [Job 688] Start rendering...
D [25/Aug/2012:17:32:38 +0200] [Job 688] Set job-printer-state-message to "Start rendering...", current level=INFO
I [25/Aug/2012:17:32:38 +0200] [Job 688] Processing page 1...
D [25/Aug/2012:17:32:38 +0200] [Job 688] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [25/Aug/2012:17:32:38 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:32:38 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 4096 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 4096 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Read 4096 bytes of print data...
D [25/Aug/2012:17:32:39 +0200] [Job 688] Wrote 4096 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 4096 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 4096 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 4096 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Wrote 4096 bytes of print data...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Read 8192 bytes of print data...
I [25/Aug/2012:17:32:40 +0200] [Job 688] Processing page 2...
D [25/Aug/2012:17:32:40 +0200] [Job 688] Set job-printer-state-message to "Processing page 2...", current level=INFO
D [25/Aug/2012:17:32:40 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:32:40 +0200] Discarding unused printer-state-changed event...
I [25/Aug/2012:17:32:40 +0200] [Job 688] Rendering completed
D [25/Aug/2012:17:32:40 +0200] [Job 688] Set job-printer-state-message to "Rendering completed", current level=INFO
D [25/Aug/2012:17:32:40 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:32:40 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:40 +0200] PID 2455 (/usr/lib/cups/filter/gstoraster) exited with no errors.
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] PID 2456 (/opt/epson-inkjet-printer-workforce-635-nx625-series/cups/lib/filter/epson_inkjet_printer_filter) exited with no errors.
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 8192 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Read 6495 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Wrote 6495 bytes of print data...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Sent 211295 bytes...
D [25/Aug/2012:17:32:41 +0200] [Job 688] Waiting for read thread to exit...
D [25/Aug/2012:17:32:41 +0200] PID 2457 (/usr/lib/cups/backend/usb) exited with no errors.
D [25/Aug/2012:17:32:41 +0200] Discarding unused job-completed event...
I [25/Aug/2012:17:32:41 +0200] [Job 688] Job completed.
D [25/Aug/2012:17:32:41 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:32:41 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [25/Aug/2012:17:32:41 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [25/Aug/2012:17:32:41 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:32:42 +0200] [Job 688] Unloading...
D [25/Aug/2012:17:32:56 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [25/Aug/2012:17:32:56 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.2:631
D [25/Aug/2012:17:32:56 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [25/Aug/2012:17:32:56 +0200] cupsdNetIFUpdate: "eth0" = [v1.fe80::2e0:81ff:fe56:f37a+eth0]:631


(Next print now)


I [25/Aug/2012:17:33:09 +0200] Saving job.cache...
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Printing jobs and dirty files"
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:09 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:09 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:09 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:09 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [25/Aug/2012:17:33:09 +0200] CUPS-Get-Default
D [25/Aug/2012:17:33:09 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:09 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:09 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:09 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:09 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [25/Aug/2012:17:33:09 +0200] CUPS-Get-Default
D [25/Aug/2012:17:33:09 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:09 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:09 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:33:09 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:09 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:09 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:10 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:10 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 GET /printers/Epson_Stylus_Office_B42WD.ppd HTTP/1.1
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:10 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:10 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:10 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:10 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:10 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:10 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:10 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:10 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:10 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:10 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:11 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:11 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:11 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:11 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:11 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:11 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:33:11 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:11 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:11 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:11 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:11 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [25/Aug/2012:17:33:11 +0200] CUPS-Get-Printers
D [25/Aug/2012:17:33:11 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [25/Aug/2012:17:33:11 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [25/Aug/2012:17:33:11 +0200] cupsdCloseClient: 18
D [25/Aug/2012:17:33:11 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [25/Aug/2012:17:33:12 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [25/Aug/2012:17:33:12 +0200] cupsdReadClient: 17 POST /printers/Epson_Stylus_Office_B42WD HTTP/1.1
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [25/Aug/2012:17:33:12 +0200] cupsdAuthorize: No authentication data provided.
D [25/Aug/2012:17:33:12 +0200] cupsdReadClient: 17 1.1 Print-Job 1
D [25/Aug/2012:17:33:12 +0200] Print-Job ipp://localhost:631/printers/Epson_Stylus_Office_B42WD
D [25/Aug/2012:17:33:12 +0200] [Job ???] Auto-typing file...
I [25/Aug/2012:17:33:12 +0200] [Job ???] Request file type is application/pdf.
D [25/Aug/2012:17:33:12 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"
D [25/Aug/2012:17:33:12 +0200] add_job: requesting-user-name="alain"
I [25/Aug/2012:17:33:12 +0200] [Job 689] Adding start banner page "none".
D [25/Aug/2012:17:33:12 +0200] Discarding unused job-created event...
D [25/Aug/2012:17:33:12 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [25/Aug/2012:17:33:12 +0200] [Job 689] Adding end banner page "none".
I [25/Aug/2012:17:33:12 +0200] [Job 689] File of type application/pdf queued by "alain".
D [25/Aug/2012:17:33:12 +0200] [Job 689] hold_until=0
I [25/Aug/2012:17:33:12 +0200] [Job 689] Queued on "Epson_Stylus_Office_B42WD" by "alain".
D [25/Aug/2012:17:33:12 +0200] cupsdMarkDirty(----J-)
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [25/Aug/2012:17:33:12 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:33:12 +0200] [Job 689] job-sheets=none,none
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[0]="Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[1]="689"
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[2]="alain"
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[3]="Tâches - CUPS 1.5.3"
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[4]="1"
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[5]="Rotate180=Off DensityWatermark=Level4 SizeWatermark=70 BrightnessValue=0 PrintQuality=Text number-up=1 Watermark=None YellowValue=0 PageSize=Letter ReduceEnlarge=Off OutputPaper=A4 MirrorImage=Off CyanValue=0 PositionWatermark=Center PosterPrinting=Off GammaValue=2.2 ScaleRatio=100 AdjustPrintDensity=TextPhoto Color=Grayscale Duplex=DuplexNoTumble MediaType=PLAIN ColurWatermark=Red ContrastValue=0 MagentaValue=0 SaturationValue=0 CorrectionColor=EPSONVivid FaceDown=Off Borderless=Off job-uuid=urn:uuid:639dd864-5961-31e2-63fb-7a4dd912a86a job-originating-host-name=localhost time-at-creation=1345908792 time-at-processing=1345908792"
D [25/Aug/2012:17:33:12 +0200] [Job 689] argv[6]="/var/spool/cups/d00689-001"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[8]="HOME=/var/spool/cups/tmp"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[10]="SERVER_ADMIN=root@alain-desktop"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[11]="SOFTWARE=CUPS/1.5.3"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[13]="USER=root"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[16]="IPP_PORT=631"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[17]="CHARSET=utf-8"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[18]="LANG=fr_FR.UTF-8"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[19]="PPD=/etc/cups/ppd/Epson_Stylus_Office_B42WD.ppd"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[20]="RIP_MAX_CACHE=128m"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[21]="CONTENT_TYPE=application/pdf"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[22]="DEVICE_URI=usb://EPSON/Stylus%20Office%20B42WD?serial=4D4734593031313566"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[23]="PRINTER_INFO=Epson Stylus Office B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[24]="PRINTER_LOCATION="
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[25]="PRINTER=Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[26]="PRINTER_STATE_REASONS=none"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[27]="CUPS_FILETYPE=document"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[28]="FINAL_CONTENT_TYPE=printer/Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[29]="AUTH_I****"
I [25/Aug/2012:17:33:12 +0200] [Job 689] Started filter /usr/lib/cups/filter/pdftopdf (PID 2463)
I [25/Aug/2012:17:33:12 +0200] [Job 689] Started filter /usr/lib/cups/filter/gstoraster (PID 2464)
I [25/Aug/2012:17:33:12 +0200] [Job 689] Started filter /opt/epson-inkjet-printer-workforce-635-nx625-series/cups/lib/filter/epson_inkjet_printer_filter (PID 2465)
I [25/Aug/2012:17:33:12 +0200] [Job 689] Started backend /usr/lib/cups/backend/usb (PID 2466)
D [25/Aug/2012:17:33:12 +0200] Discarding unused job-state-changed event...
D [25/Aug/2012:17:33:12 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/Epson_Stylus_Office_B42WD) from localhost
D [25/Aug/2012:17:33:12 +0200] [Job 689] libusb_get_device_list=6
D [25/Aug/2012:17:33:12 +0200] [Job 689] STATE: +connecting-to-device
D [25/Aug/2012:17:33:12 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [25/Aug/2012:17:33:12 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [25/Aug/2012:17:33:12 +0200] cupsdCloseClient: 17
D [25/Aug/2012:17:33:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [25/Aug/2012:17:33:12 +0200] [Job 689] STATE: -connecting-to-device
D [25/Aug/2012:17:33:12 +0200] Discarding unused printer-state-changed event...
I [25/Aug/2012:17:33:12 +0200] [Job 689] Sending data to printer.
D [25/Aug/2012:17:33:12 +0200] [Job 689] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [25/Aug/2012:17:33:12 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:33:12 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:33:12 +0200] PID 2463 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [25/Aug/2012:17:33:12 +0200] [Job 689] PPD uses qualifier 'RGB.PLAIN.'
D [25/Aug/2012:17:33:12 +0200] [Job 689] Calling FindDeviceById(Epson_Stylus_Office_B42WD)
D [25/Aug/2012:17:33:12 +0200] [Job 689] Failed to send: org.freedesktop.ColorManager.Failed:device id 'Epson_Stylus_Office_B42WD' does not exists
D [25/Aug/2012:17:33:12 +0200] [Job 689] Failed to get profile filename!
I [25/Aug/2012:17:33:12 +0200] [Job 689] no profiles specified in PPD
D [25/Aug/2012:17:33:12 +0200] [Job 689] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [25/Aug/2012:17:33:12 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:33:12 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:33:12 +0200] [Job 689] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -r360x360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=0 -dcupsCompression=1 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c -f -_
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[8]="HOME=/var/spool/cups/tmp"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[10]="SERVER_ADMIN=root@alain-desktop"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[11]="SOFTWARE=CUPS/1.5.3"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[12]="USER=root"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[15]="IPP_PORT=631"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[16]="CHARSET=utf-8"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[17]="LANG=fr_FR.UTF-8"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[18]="PPD=/etc/cups/ppd/Epson_Stylus_Office_B42WD.ppd"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[19]="RIP_MAX_CACHE=128m"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[20]="CONTENT_TYPE=application/pdf"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[21]="DEVICE_URI=usb://EPSON/Stylus%20Office%20B42WD?serial=4D4734593031313566"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[22]="PRINTER_INFO=Epson Stylus Office B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[23]="PRINTER_LOCATION="
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[24]="PRINTER=Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[25]="PRINTER_STATE_REASONS=none"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[26]="CUPS_FILETYPE=document"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[27]="FINAL_CONTENT_TYPE=printer/Epson_Stylus_Office_B42WD"
D [25/Aug/2012:17:33:12 +0200] [Job 689] envp[28]="AUTH_INFO_REQUIRED=none"
I [25/Aug/2012:17:33:12 +0200] [Job 689] Start rendering...
D [25/Aug/2012:17:33:12 +0200] [Job 689] Set job-printer-state-message to "Start rendering...", current level=INFO
I [25/Aug/2012:17:33:12 +0200] [Job 689] Processing page 1...
D [25/Aug/2012:17:33:12 +0200] [Job 689] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [25/Aug/2012:17:33:12 +0200] Discarding unused job-progress event...
D [25/Aug/2012:17:33:12 +0200] Discarding unused printer-state-changed event...
D [25/Aug/2012:17:33:13 +0200] [Job 689] Read 4096 bytes of print data...
D [25/Aug/2012:17:33:27 +0200] Report: clients=1
D [25/Aug/2012:17:33:27 +0200] Report: jobs=40
D [25/Aug/2012:17:33:27 +0200] Report: jobs-active=1
D [25/Aug/2012:17:33:27 +0200] Report: printers=2
D [25/Aug/2012:17:33:27 +0200] Report: printers-implicit=0
D [25/Aug/2012:17:33:27 +0200] Report: stringpool-string-count=4681
D [25/Aug/2012:17:33:27 +0200] Report: stringpool-alloc-bytes=13704
D [25/Aug/2012:17:33:27 +0200] Report: stringpool-total-bytes=88880
I [25/Aug/2012:17:33:43 +0200] Saving job.cache...
D [25/Aug/2012:17:33:43 +0200] cupsdSetBusyState: newbusy="Printing jobs", busy="Dirty files"
D [25/Aug/2012:17:33:58 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [25/Aug/2012:17:33:58 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.2:631
D [25/Aug/2012:17:33:58 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [25/Aug/2012:17:33:58 +0200] cupsdNetIFUpdate: "eth0" = [v1.fe80::2e0:81ff:fe56:f37a+eth0]:631
D [25/Aug/2012:17:34:13 +0200] [Job 689] Got USB transaction timeout during write.
D [25/Aug/2012:17:34:29 +0200] Report: clients=1
D [25/Aug/2012:17:34:29 +0200] Report: jobs=40
D [25/Aug/2012:17:34:29 +0200] Report: jobs-active=1
D [25/Aug/2012:17:34:29 +0200] Report: printers=2
D [25/Aug/2012:17:34:29 +0200] Report: printers-implicit=0
D [25/Aug/2012:17:34:29 +0200] Report: stringpool-string-count=4681
D [25/Aug/2012:17:34:29 +0200] Report: stringpool-alloc-bytes=13704
D [25/Aug/2012:17:34:29 +0200] Report: stringpool-total-bytes=88880
D [25/Aug/2012:17:35:00 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [25/Aug/2012:17:35:00 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.2:631
D [25/Aug/2012:17:35:00 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [25/Aug/2012:17:35:00 +0200] cupsdNetIFUpdate: "eth0" = [v1.fe80::2e0:81ff:fe56:f37a+eth0]:631

```

---

### Post by dargaud on 2012-09-13
Well, I still have this problem even after the latest round of cups upgrade and an "aptitude reinstall cups". I'm using the TurboPrint driver in the meanwhile.

---


---
title: "Printer detected, but won't accept print jobs"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by Turin Turambar on 2006-06-08
I have a Canon i350 printer with Turboprint 1.89 drivers. They worked great for Hoary and Breezy, but now I have some troubles with it...
It detects the printer (I can even check the ink level), but won't let me print anything. It just says "lp: Destination "Canon" is not accepting jobs."

I checked the cups error_log and here's what it says:

```
D [09/Jun/2006:01:12:55 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:12:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:12:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:12:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:12:55 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:12:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:00 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:00 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:05 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:05 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:10 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:10 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:15 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:15 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:20 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:20 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:25 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:25 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:30 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:30 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:35 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:35 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:40 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:40 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:45 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:45 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:50 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:50 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:55 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:13:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:13:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:13:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:13:55 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:13:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:00 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:00 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:05 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:05 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:10 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:10 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:15 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:15 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:20 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:20 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:25 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:25 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:30 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:30 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:35 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:35 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:40 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:40 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:45 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:45 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:50 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:50 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:55 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:14:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:14:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:14:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:14:55 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:14:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:00 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:00 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:05 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:05 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:10 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:10 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:15 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:15 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:20 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:20 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:25 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:25 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:30 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:30 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:35 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:35 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:40 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:40 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:45 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:45 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:50 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:50 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:55 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:15:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:15:55 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:15:55 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:15:55 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:15:55 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:00 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:00 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:00 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:00 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:00 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:05 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:05 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:05 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:05 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:05 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:10 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:10 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:10 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:10 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:10 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:15 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:15 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:15 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:15 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:15 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:20 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:20 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:20 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:20 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:20 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:25 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:25 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:25 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:25 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:25 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:30 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:30 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:30 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:30 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:30 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:35 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:35 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:35 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:35 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:35 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:40 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:40 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:40 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:40 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:40 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:45 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:45 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:45 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:45 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:45 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:50 +0200] CUPS-Get-Printers
D [09/Jun/2006:01:16:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [09/Jun/2006:01:16:50 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [09/Jun/2006:01:16:50 +0200] cupsdAuthorize: No authentication data provided.
D [09/Jun/2006:01:16:50 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon
D [09/Jun/2006:01:16:50 +0200] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
```

What exactly is wrong? I cannot understand, what authorisation??!

---

### Post by Turin Turambar on 2006-06-08
I fixed it. It REQUIRES a new Turboprint 1.94-3 driver, because Dapper is using new version of CUPS, that is not supported by older turboprint drivers.

---

### Post by lakelovers on 2006-06-09
[QUOTE=Turin Turambar]I fixed it. It REQUIRES a new Turboprint 1.94-3 driver, because Dapper is using new version of CUPS, that is not supported by older turboprint drivers.[/QUOTE]

Many thanks, Turin. . . I've been battling this situation for several days, and not finding a solution to my posts. Anyway, I followed your lead, downloaded 1.94-3, and now I'm back in business. Thanks, again.
Jerry

---


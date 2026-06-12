---
title: "Lexmark Z705 printing problem"
date: 2009-08-21
forum: Hardware
---

### Post by Eremis on 2009-08-21
Hi!

I downloaded z700 printing drivers from: [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/) and converted them into .deb using "alien". last time i done this (ububntu 8.04) it worked fine, and everything worked, however now when I installed the same drivers, and try to print something I get an error, after runing the diagnostic I got 2 files: 1. error repot  2. troubleshoot report, I tried attaching them both to this thread but they are too big.....

I will just paste them insted....

Can someone help me? :confused: Any ideas?

-- Thanks


Error report:
```
D [21/Aug/2009:15:11:58 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:11:58 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:11:58 -0400] Get-Jobs ipp://localhost/printers/
D [21/Aug/2009:15:11:58 -0400] [Job 1] Loading attributes...
D [21/Aug/2009:15:11:58 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:11:58 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:11:58 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:11:58 -0400] Get-Jobs ipp://localhost/printers/
D [21/Aug/2009:15:11:58 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:11:58 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:11:58 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:11:58 -0400] Create-Printer-Subscription /
D [21/Aug/2009:15:11:58 -0400] cupsdCreateSubscription(con=0xb9f2ab98(8), uri="/")
D [21/Aug/2009:15:11:58 -0400] pullmethod="ippget"
D [21/Aug/2009:15:11:58 -0400] notify-lease-duration=86400
D [21/Aug/2009:15:11:58 -0400] notify-time-interval=0
D [21/Aug/2009:15:11:58 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [21/Aug/2009:15:11:58 -0400] Added subscription 6 for server
I [21/Aug/2009:15:11:58 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:11:58 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:11:59 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:11:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:11:59 -0400] Get-Notifications /
D [21/Aug/2009:15:11:59 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:11:59 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:10 -0400] cupsdReadClient: 8 POST /jobs/ HTTP/1.1
D [21/Aug/2009:15:12:10 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:10 -0400] Cancel-Job ipp://localhost/jobs/1
D [21/Aug/2009:15:12:10 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
I [21/Aug/2009:15:12:10 -0400] Saving subscriptions.conf...
I [21/Aug/2009:15:12:10 -0400] [Job 1] Canceled by "andriy".
D [21/Aug/2009:15:12:10 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:12 -0400] cupsdReadClient: 8 POST /jobs/ HTTP/1.1
D [21/Aug/2009:15:12:12 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:12 -0400] Cancel-Job ipp://localhost/jobs/1
D [21/Aug/2009:15:12:12 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:12 -0400] Cancel-Job client-error-not-possible: Job #1 is already canceled - can't cancel.
D [21/Aug/2009:15:12:12 -0400] cupsdProcessIPPRequest: 8 status_code=404 (client-error-not-possible)
D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 9 POST /printers/Z700-P700-Series HTTP/1.1
D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:16 -0400] Print-Job ipp://localhost/printers/Z700-P700-Series
D [21/Aug/2009:15:12:16 -0400] [Job ???] Auto-typing file...
I [21/Aug/2009:15:12:16 -0400] [Job ???] Request file type is application/postscript.
D [21/Aug/2009:15:12:16 -0400] add_job: requesting-user-name="andriy"
D [21/Aug/2009:15:12:16 -0400] Adding default job-sheets values "none,none"...
I [21/Aug/2009:15:12:16 -0400] [Job 2] Adding start banner page "none".
I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...
I [21/Aug/2009:15:12:16 -0400] [Job 2] Adding end banner page "none".
I [21/Aug/2009:15:12:16 -0400] [Job 2] File of type application/postscript queued by "andriy".
D [21/Aug/2009:15:12:16 -0400] [Job 2] hold_until=0
I [21/Aug/2009:15:12:16 -0400] [Job 2] Queued on "Z700-P700-Series" by "andriy".
I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:12:16 -0400] [Job 2] job-sheets=none,none
D [21/Aug/2009:15:12:16 -0400] [Job 2] banner_page = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[0]="Z700-P700-Series"
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[1]="2"
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[2]="andriy"
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[3]="Test Page"
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[4]="1"
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[5]="job-uuid=urn:uuid:e7c24190-4c1e-3ec6-4e3e-e015139b262a"
D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[6]="/var/spool/cups/d00002-001"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[9]="SERVER_ADMIN=root@linux-machine"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.9"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[12]="TZ=America/New_York"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[13]="USER=root"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[16]="IPP_PORT=631"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[17]="CHARSET=utf-8"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[18]="LANG=en_US.UTF8"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[19]="PPD=/etc/cups/ppd/Z700-P700-Series.ppd"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[20]="RIP_MAX_CACHE=8m"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[21]="CONTENT_TYPE=application/postscript"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[22]="DEVICE_URI=usb://Lexmark%20/Z700-P700%20Series"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[23]="PRINTER=Z700-P700-Series"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[24]="FINAL_CONTENT_TYPE=printer/Z700-P700-Series"
I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/pstopdf (PID 20280)
I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/pdftopdf (PID 20283)
I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/pdftoraster (PID 20284)
I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/rastertoz700 (PID 20287)
I [21/Aug/2009:15:12:16 -0400] [Job 2] Started backend /usr/lib/cups/backend/usb (PID 20288)
I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
E [21/Aug/2009:15:12:16 -0400] PID 20287 (/usr/lib/cups/filter/rastertoz700) stopped with status 127!
D [21/Aug/2009:15:12:16 -0400] [Job 2] pstopdf 6 args: 2 andriy Test Page 1 job-uuid=urn:uuid:e7c24190-4c1e-3ec6-4e3e-e015139b262a /var/spool/cups/d00002-001
D [21/Aug/2009:15:12:16 -0400] [Job 2] PPD: /etc/cups/ppd/Z700-P700-Series.ppd
D [21/Aug/2009:15:12:16 -0400] [Job 2] Z700-P700-Series: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Printer using device file "/dev/usblp0"...
D [21/Aug/2009:15:12:16 -0400] [Job 2] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb7fd3a80)
I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:12:16 -0400] PID 20288 (/usr/lib/cups/backend/usb) exited with no errors.
D [21/Aug/2009:15:12:16 -0400] [Job 2] Resolution:
D [21/Aug/2009:15:12:16 -0400] [Job 2] Page size: Letter
D [21/Aug/2009:15:12:16 -0400] [Job 2] Width: 612, height: 792, absolute margins: 18, 36, 594, 787
D [21/Aug/2009:15:12:16 -0400] [Job 2] Relative margins: 18, 36, 18, 5
D [21/Aug/2009:15:12:16 -0400] [Job 2] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [21/Aug/2009:15:12:16 -0400] [Job 2] PostScript to be injected:
D [21/Aug/2009:15:12:16 -0400] [Job 2] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [21/Aug/2009:15:12:16 -0400] [Job 2] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:16 -0400] Get-Notifications /
D [21/Aug/2009:15:12:16 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:16 -0400] Get-Jobs ipp://localhost/printers/
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdCloseClient: 13
D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:16 -0400] Get-Notifications /
D [21/Aug/2009:15:12:16 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:16 -0400] Get-Job-Attributes ipp://localhost/jobs/2
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 14 POST / HTTP/1.1
E [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: Local authentication certificate not found!
D [21/Aug/2009:15:12:16 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 14 POST / HTTP/1.1
E [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: Local authentication certificate not found!
D [21/Aug/2009:15:12:16 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:16 -0400] Get-Notifications /
D [21/Aug/2009:15:12:16 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 14 POST / HTTP/1.1
E [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: Local authentication certificate not found!
D [21/Aug/2009:15:12:16 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series
D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:16 -0400] cupsdCloseClient: 13
D [21/Aug/2009:15:12:16 -0400] cupsdCloseClient: 12
D [21/Aug/2009:15:12:16 -0400] PID 20280 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [21/Aug/2009:15:12:16 -0400] [Job 2] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -dcupsRowStep=3 -scupsPageSizeName=Letter -c -f -_
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[9]="SERVER_ADMIN=root@linux-machine"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.9"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[11]="TZ=America/New_York"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[12]="USER=root"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[15]="IPP_PORT=631"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[16]="CHARSET=utf-8"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[17]="LANG=en_US.UTF8"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[18]="PPD=/etc/cups/ppd/Z700-P700-Series.ppd"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[19]="RIP_MAX_CACHE=8m"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[20]="CONTENT_TYPE=application/postscript"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[21]="DEVICE_URI=usb://Lexmark%20/Z700-P700%20Series"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[22]="PRINTER=Z700-P700-Series"
D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[23]="FINAL_CONTENT_TYPE=printer/Z700-P700-Series"
D [21/Aug/2009:15:12:16 -0400] PID 20283 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 1, depth = 1
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 3, cupsColorOrder = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 1, cupsBitsPerColor = 1
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 1, dither_grays = 2
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 0, dither_colors = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] Updating PageSize to [612 792]...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting initial media size, [612 792] = 5100x6600 pixels...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsBitsPerColor to 8...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsColorOrder to 0...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsColorSpace to 1...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsCompression to 1...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsRowStep to 3...
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsPageSizeName to "Letter"...
D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting initial media size, [612 792] = 5100x6600 pixels...
D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting LeadingEdge to 0...
D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:16 -0400] [Job 2] Updating PageSize to [612 792]...
D [21/Aug/2009:15:12:16 -0400] [Job 2] size = Letter
D [21/Aug/2009:15:12:16 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]
D [21/Aug/2009:15:12:17 -0400] PID 20284 (/usr/lib/cups/filter/pdftoraster) exited with no errors.
D [21/Aug/2009:15:12:17 -0400] [Job 2] Setting LeadingEdge to 0...
D [21/Aug/2009:15:12:17 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:17 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:17 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:17 -0400] [Job 2] Setting LeadingEdge to 0...
D [21/Aug/2009:15:12:17 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:17 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:17 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:17 -0400] [Job 2] Updating PageSize to [612 792]...
D [21/Aug/2009:15:12:17 -0400] [Job 2] size = Letter
D [21/Aug/2009:15:12:17 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]
D [21/Aug/2009:15:12:17 -0400] [Job 2] cups_print_chunked - flip = 0, height = 6258
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceDistance to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceMedia to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Collate to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting CutMedia to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Duplex to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Jog to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting LeadingEdge to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Margins to 0 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting MirrorPrint to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting NegativePrint to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting OutputFaceUp to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Separations to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting TraySwitch to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Tumble to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMediaType to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBitsPerColor to 8...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorOrder to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorSpace to 1...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsCompression to 1...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowCount to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowFeed to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowStep to 3...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBorderlessScalingFactor to 1.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger0 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger1 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger2 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger3 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger4 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger5 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger6 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger7 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger8 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger9 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger10 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger11 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger12 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger13 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger14 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger15 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal0 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal1 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal2 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal3 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal4 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal5 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal6 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal7 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal8 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal9 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal10 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal11 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal12 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal13 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal14 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal15 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString0 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString1 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString2 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString3 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString4 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString5 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString6 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString7 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString8 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString9 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString10 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString11 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString12 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString13 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString14 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString15 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMarkerType to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRenderingIntent to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsPageSizeName to "Letter"...
D [21/Aug/2009:15:12:18 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:18 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:18 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:18 -0400] [Job 2] Updating PageSize to [612 792]...
D [21/Aug/2009:15:12:18 -0400] [Job 2] size = Letter
D [21/Aug/2009:15:12:18 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceDistance to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceMedia to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Collate to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting CutMedia to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Duplex to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Jog to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting LeadingEdge to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Margins to 0 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting MirrorPrint to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting NegativePrint to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting OutputFaceUp to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Separations to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting TraySwitch to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Tumble to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMediaType to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBitsPerColor to 8...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorOrder to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorSpace to 1...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsCompression to 1...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowCount to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowFeed to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowStep to 3...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBorderlessScalingFactor to 1.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger0 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger1 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger2 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger3 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger4 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger5 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger6 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger7 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger8 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger9 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger10 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger11 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger12 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger13 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger14 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger15 to 0...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal0 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal1 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal2 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal3 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal4 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal5 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal6 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal7 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal8 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal9 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal10 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal11 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal12 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal13 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal14 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal15 to 0.0000...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString0 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString1 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString2 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString3 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString4 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString5 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString6 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString7 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString8 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString9 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString10 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString11 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString12 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString13 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString14 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString15 to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMarkerType to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRenderingIntent to ""...
D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsPageSizeName to "Letter"...
D [21/Aug/2009:15:12:18 -0400] [Job 2] num_components = 3, depth = 24
D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0
D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [21/Aug/2009:15:12:18 -0400] [Job 2] max_gray = 0, dither_grays = 0
D [21/Aug/2009:15:12:18 -0400] [Job 2] max_color = 255, dither_colors = 256
D [21/Aug/2009:15:12:18 -0400] [Job 2] Updating PageSize to [612 792]...
D [21/Aug/2009:15:12:18 -0400] [Job 2] size = Letter
D [21/Aug/2009:15:12:18 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]
D [21/Aug/2009:15:12:18 -0400] [Job 2] File 0 is complete.
E [21/Aug/2009:15:12:18 -0400] [Job 2] Job stopped due to filter errors.
I [21/Aug/2009:15:12:18 -0400] Saving subscriptions.conf...
I [21/Aug/2009:15:12:18 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:18 -0400] Get-Jobs ipp://localhost/printers/
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 12
D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:18 -0400] Get-Notifications /
D [21/Aug/2009:15:12:18 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 9
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:18 -0400] Get-Printer-Attributes ipp://linux-machine:631/printers/Z700-P700-Series
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:18 -0400] Get-Job-Attributes ipp://localhost/jobs/2
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 9 POST / HTTP/1.1
D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:18 -0400] Get-Notifications /
D [21/Aug/2009:15:12:18 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 14 POST / HTTP/1.1
E [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: Local authentication certificate not found!
D [21/Aug/2009:15:12:18 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 12
D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 9
D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:18 -0400] Get-Notifications /
D [21/Aug/2009:15:12:18 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:19 -0400] [Job 2] Unloading...
D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:23 -0400] Get-Job-Attributes ipp://localhost/jobs/1
D [21/Aug/2009:15:12:23 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:23 -0400] Get-Job-Attributes ipp://localhost/jobs/2
D [21/Aug/2009:15:12:23 -0400] [Job 2] Loading attributes...
D [21/Aug/2009:15:12:23 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.
D [21/Aug/2009:15:12:23 -0400] Cancel-Subscription /
D [21/Aug/2009:15:12:23 -0400] cupsdIsAuthorized: requesting-user-name="andriy"
I [21/Aug/2009:15:12:23 -0400] Saving subscriptions.conf...
D [21/Aug/2009:15:12:23 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [21/Aug/2009:15:12:23 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1
D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.
```

Trouble shoot report:
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Z700-P700-Series (default)>,
 'cups_instance': None,
 'cups_queue': 'Z700-P700-Series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark%20/Z700-P700%20Series',
                       'printer-info': u'Lexmark  Z700-P700 Series',
                       'printer-is-shared': True,
                       'printer-location': u'linux-machine',
                       'printer-make-and-model': u'Lexmark Z700 v1.0-1',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/rastertoz700 failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Z700-P700-Series'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'Others': {u'ColorModel': u'Color',
                                           u'Inkset': u'CMYK',
                                           u'PrintQuality': u'Normal'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': 'MFG:Lexmark ;CMD:CPDNPA001;MODEL:Z700-P700 Series;CLASS:Printer;DES:Lexmark Z700-P700 Series;COMMENT:021127-1;\x1b{',
                      'device-info': u'Lexmark Z700-P700 Series USB #1',
                      'device-make-and-model': u'Lexmark Z700-P700 Series'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/rastertoz700 failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 1928L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': '21/Aug/2009:15:12:16 +0000',
 'test_page_job_status': [(True,
                           1,
                           'Z700-P700-Series',
                           'Test Page',
                           'Canceled',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 1,
                            'job-k-octets': 150,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/1',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'andriy',
                            'job-preserved': False,
                            'job-printer-state-message': u'/usr/lib/cups/filter/rastertoz700 failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1250881943,
                            'job-printer-uri': u'ipp://linux-machine:631/printers/Z700-P700-Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/1',
                            'job-uuid': u'urn:uuid:ab6d0c35-57ac-3266-7896-852a8372934f',
                            'printer-uri': u'ipp://localhost/printers/Z700-P700-Series',
                            'time-at-completed': 1250881930,
                            'time-at-creation': 1250881825,
                            'time-at-processing': 1250881825}),
                          (True,
                           2,
                           'Z700-P700-Series',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 2,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/2',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'andriy',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/rastertoz700 failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1250881943,
                            'job-printer-uri': u'ipp://linux-machine:631/printers/Z700-P700-Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/2',
                            'job-uuid': u'urn:uuid:e7c24190-4c1e-3ec6-4e3e-e015139b262a',
                            'printer-uri': u'ipp://localhost/printers/Z700-P700-Series',
                            'time-at-completed': None,
                            'time-at-creation': 1250881936,
                            'time-at-processing': 1250881936})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [21/Aug/2009:15:11:58 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:11:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:11:58 -0400] Get-Jobs ipp://localhost/printers/',
               'D [21/Aug/2009:15:11:58 -0400] [Job 1] Loading attributes...',
               'D [21/Aug/2009:15:11:58 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:11:58 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:11:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:11:58 -0400] Get-Jobs ipp://localhost/printers/',
               'D [21/Aug/2009:15:11:58 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:11:58 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:11:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:11:58 -0400] Create-Printer-Subscription /',
               'D [21/Aug/2009:15:11:58 -0400] cupsdCreateSubscription(con=0xb9f2ab98(8), uri="/")',
               'D [21/Aug/2009:15:11:58 -0400] pullmethod="ippget"',
               'D [21/Aug/2009:15:11:58 -0400] notify-lease-duration=86400',
               'D [21/Aug/2009:15:11:58 -0400] notify-time-interval=0',
               'D [21/Aug/2009:15:11:58 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [21/Aug/2009:15:11:58 -0400] Added subscription 6 for server',
               'I [21/Aug/2009:15:11:58 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:11:58 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:11:59 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:11:59 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:11:59 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:11:59 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:11:59 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:10 -0400] cupsdReadClient: 8 POST /jobs/ HTTP/1.1',
               'D [21/Aug/2009:15:12:10 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:10 -0400] Cancel-Job ipp://localhost/jobs/1',
               'D [21/Aug/2009:15:12:10 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'I [21/Aug/2009:15:12:10 -0400] Saving subscriptions.conf...',
               'I [21/Aug/2009:15:12:10 -0400] [Job 1] Canceled by "andriy".',
               'D [21/Aug/2009:15:12:10 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:12 -0400] cupsdReadClient: 8 POST /jobs/ HTTP/1.1',
               'D [21/Aug/2009:15:12:12 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:12 -0400] Cancel-Job ipp://localhost/jobs/1',
               'D [21/Aug/2009:15:12:12 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               "D [21/Aug/2009:15:12:12 -0400] Cancel-Job client-error-not-possible: Job #1 is already canceled - can't cancel.",
               'D [21/Aug/2009:15:12:12 -0400] cupsdProcessIPPRequest: 8 status_code=404 (client-error-not-possible)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 9 POST /printers/Z700-P700-Series HTTP/1.1',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:16 -0400] Print-Job ipp://localhost/printers/Z700-P700-Series',
               'D [21/Aug/2009:15:12:16 -0400] [Job ???] Auto-typing file...',
               'I [21/Aug/2009:15:12:16 -0400] [Job ???] Request file type is application/postscript.',
               'D [21/Aug/2009:15:12:16 -0400] add_job: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:16 -0400] Adding default job-sheets values "none,none"...',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Adding start banner page "none".',
               'I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Adding end banner page "none".',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] File of type application/postscript queued by "andriy".',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] hold_until=0',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Queued on "Z700-P700-Series" by "andriy".',
               'I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] job-sheets=none,none',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] banner_page = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[0]="Z700-P700-Series"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[1]="2"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[2]="andriy"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[3]="Test Page"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[4]="1"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[5]="job-uuid=urn:uuid:e7c24190-4c1e-3ec6-4e3e-e015139b262a"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] argv[6]="/var/spool/cups/d00002-001"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[9]="SERVER_ADMIN=root@linux-machine"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[12]="TZ=America/New_York"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[13]="USER=root"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[16]="IPP_PORT=631"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[17]="CHARSET=utf-8"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[18]="LANG=en_US.UTF8"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[19]="PPD=/etc/cups/ppd/Z700-P700-Series.ppd"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[20]="RIP_MAX_CACHE=8m"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[22]="DEVICE_URI=usb://Lexmark%20/Z700-P700%20Series"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[23]="PRINTER=Z700-P700-Series"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[24]="FINAL_CONTENT_TYPE=printer/Z700-P700-Series"',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/pstopdf (PID 20280)',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/pdftopdf (PID 20283)',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/pdftoraster (PID 20284)',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Started filter /usr/lib/cups/filter/rastertoz700 (PID 20287)',
               'I [21/Aug/2009:15:12:16 -0400] [Job 2] Started backend /usr/lib/cups/backend/usb (PID 20288)',
               'I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'E [21/Aug/2009:15:12:16 -0400] PID 20287 (/usr/lib/cups/filter/rastertoz700) stopped with status 127!',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] pstopdf 6 args: 2 andriy Test Page 1 job-uuid=urn:uuid:e7c24190-4c1e-3ec6-4e3e-e015139b262a /var/spool/cups/d00002-001',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] PPD: /etc/cups/ppd/Z700-P700-Series.ppd',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Z700-P700-Series: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory',
               'I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Printer using device file "/dev/usblp0"...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb7fd3a80)',
               'I [21/Aug/2009:15:12:16 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:12:16 -0400] PID 20288 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Resolution:',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Page size: Letter',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Width: 612, height: 792, absolute margins: 18, 36, 594, 787',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Relative margins: 18, 36, 18, 5',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] PostScript to be injected:',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:16 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:12:16 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:16 -0400] Get-Jobs ipp://localhost/printers/',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdCloseClient: 13',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:16 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:12:16 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:16 -0400] Get-Job-Attributes ipp://localhost/jobs/2',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: Local authentication certificate not found!',
               'D [21/Aug/2009:15:12:16 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: Local authentication certificate not found!',
               'D [21/Aug/2009:15:12:16 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:16 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:12:16 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [21/Aug/2009:15:12:16 -0400] cupsdAuthorize: Local authentication certificate not found!',
               'D [21/Aug/2009:15:12:16 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series',
               'D [21/Aug/2009:15:12:16 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:16 -0400] cupsdCloseClient: 13',
               'D [21/Aug/2009:15:12:16 -0400] cupsdCloseClient: 12',
               'D [21/Aug/2009:15:12:16 -0400] PID 20280 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -dcupsRowStep=3 -scupsPageSizeName=Letter -c -f -_',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[9]="SERVER_ADMIN=root@linux-machine"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[11]="TZ=America/New_York"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[12]="USER=root"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[14]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[15]="IPP_PORT=631"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[16]="CHARSET=utf-8"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[17]="LANG=en_US.UTF8"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[18]="PPD=/etc/cups/ppd/Z700-P700-Series.ppd"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[19]="RIP_MAX_CACHE=8m"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[20]="CONTENT_TYPE=application/postscript"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[21]="DEVICE_URI=usb://Lexmark%20/Z700-P700%20Series"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[22]="PRINTER=Z700-P700-Series"',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] envp[23]="FINAL_CONTENT_TYPE=printer/Z700-P700-Series"',
               'D [21/Aug/2009:15:12:16 -0400] PID 20283 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 1, depth = 1',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 1, dither_grays = 2',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 0, dither_colors = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Updating PageSize to [612 792]...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsBitsPerColor to 8...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsColorOrder to 0...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsColorSpace to 1...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsCompression to 1...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsRowStep to 3...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting cupsPageSizeName to "Letter"...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Setting LeadingEdge to 0...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] Updating PageSize to [612 792]...',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] size = Letter',
               'D [21/Aug/2009:15:12:16 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]',
               'D [21/Aug/2009:15:12:17 -0400] PID 20284 (/usr/lib/cups/filter/pdftoraster) exited with no errors.',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] Setting LeadingEdge to 0...',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] Setting LeadingEdge to 0...',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] Updating PageSize to [612 792]...',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] size = Letter',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]',
               'D [21/Aug/2009:15:12:17 -0400] [Job 2] cups_print_chunked - flip = 0, height = 6258',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceDistance to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceMedia to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Collate to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting CutMedia to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Duplex to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Jog to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting LeadingEdge to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Margins to 0 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting MirrorPrint to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting NegativePrint to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting OutputFaceUp to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Separations to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting TraySwitch to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Tumble to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMediaType to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBitsPerColor to 8...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorOrder to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorSpace to 1...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsCompression to 1...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowCount to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowFeed to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowStep to 3...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBorderlessScalingFactor to 1.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger0 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger1 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger2 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger3 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger4 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger5 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger6 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger7 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger8 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger9 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger10 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger11 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger12 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger13 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger14 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger15 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal0 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal1 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal2 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal3 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal4 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal5 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal6 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal7 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal8 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal9 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal10 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal11 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal12 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal13 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal14 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal15 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString0 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString1 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString2 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString3 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString4 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString5 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString6 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString7 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString8 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString9 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString10 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString11 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString12 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString13 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString14 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString15 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMarkerType to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRenderingIntent to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsPageSizeName to "Letter"...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Updating PageSize to [612 792]...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] size = Letter',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceDistance to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting AdvanceMedia to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Collate to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting CutMedia to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Duplex to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Jog to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting LeadingEdge to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Margins to 0 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting MirrorPrint to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting NegativePrint to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting OutputFaceUp to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Separations to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting TraySwitch to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting Tumble to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMediaType to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBitsPerColor to 8...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorOrder to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsColorSpace to 1...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsCompression to 1...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowCount to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowFeed to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRowStep to 3...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsBorderlessScalingFactor to 1.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger0 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger1 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger2 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger3 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger4 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger5 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger6 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger7 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger8 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger9 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger10 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger11 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger12 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger13 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger14 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsInteger15 to 0...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal0 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal1 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal2 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal3 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal4 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal5 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal6 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal7 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal8 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal9 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal10 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal11 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal12 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal13 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal14 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsReal15 to 0.0000...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString0 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString1 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString2 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString3 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString4 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString5 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString6 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString7 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString8 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString9 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString10 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString11 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString12 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString13 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString14 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsString15 to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsMarkerType to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsRenderingIntent to ""...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Setting cupsPageSizeName to "Letter"...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] num_components = 3, depth = 24',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] max_gray = 0, dither_grays = 0',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] max_color = 255, dither_colors = 256',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] Updating PageSize to [612 792]...',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] size = Letter',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]',
               'D [21/Aug/2009:15:12:18 -0400] [Job 2] File 0 is complete.',
               'E [21/Aug/2009:15:12:18 -0400] [Job 2] Job stopped due to filter errors.',
               'I [21/Aug/2009:15:12:18 -0400] Saving subscriptions.conf...',
               'I [21/Aug/2009:15:12:18 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:18 -0400] Get-Jobs ipp://localhost/printers/',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 12',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:18 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:12:18 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 9',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:18 -0400] Get-Printer-Attributes ipp://linux-machine:631/printers/Z700-P700-Series',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:18 -0400] Get-Job-Attributes ipp://localhost/jobs/2',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:18 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:12:18 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: Local authentication certificate not found!',
               'D [21/Aug/2009:15:12:18 -0400] Get-Printer-Attributes ipp://localhost/printers/Z700-P700-Series',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 12',
               'D [21/Aug/2009:15:12:18 -0400] cupsdCloseClient: 9',
               'D [21/Aug/2009:15:12:18 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:18 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:18 -0400] Get-Notifications /',
               'D [21/Aug/2009:15:12:18 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'D [21/Aug/2009:15:12:18 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:19 -0400] [Job 2] Unloading...',
               'D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:23 -0400] Get-Job-Attributes ipp://localhost/jobs/1',
               'D [21/Aug/2009:15:12:23 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:23 -0400] Get-Job-Attributes ipp://localhost/jobs/2',
               'D [21/Aug/2009:15:12:23 -0400] [Job 2] Loading attributes...',
               'D [21/Aug/2009:15:12:23 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Aug/2009:15:12:23 -0400] Cancel-Subscription /',
               'D [21/Aug/2009:15:12:23 -0400] cupsdIsAuthorized: requesting-user-name="andriy"',
               'I [21/Aug/2009:15:12:23 -0400] Saving subscriptions.conf...',
               'D [21/Aug/2009:15:12:23 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Aug/2009:15:12:23 -0400] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [21/Aug/2009:15:12:23 -0400] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [21/Aug/2009:15:12:23 -0400] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```

---

### Post by TuxLand on 2009-09-04
These instructions assume your USB is working correctly and that you already have "alien" installed from the package manager. If this is not the case for you, search around because the instructions on how to take care of this is on the site.

go to a terminal and make a dir lexmark. I made it in my home folder so that it was accessible regardless of which kernel I booted to.

Code:

mkdir /home/*YOURUSERNAME*/lexmark

As said above, download these files (right click, save as, and save them to your newly created lexmark directory):

[http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm]("http://users.cybercity.dk/%7Edko12479/z700llpddk-2.0-1.i386.rpm")
&
[http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm]("http://users.cybercity.dk/%7Edko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm")


go back to the terminal and do the following commands:

Code:

cd /home/*YOURUSERNAME*/lexmark
sudo alien -t z700llpddk-2.0-1.i386.rpm
sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm
sudo tar xvzf  z700llpddk-2.0.tgz -C /
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz
sudo /etc/init.d/cups restart

and just to check to make sure it being recognized properly:
Code:

cd /usr/lib/cups/backend
./z700

and it should show you this or something similar:
Code:

direct z700:/dev/usblp0 "Lexmark  Lexmark Z700-P700 Series" "Lexmark Printer"

(if required install trought synaptic libstdc++.so.5)

If all is good, you can close the terminal out.

Go to SYSTEM > ADMINISTRATION > PRINTING to set up the printer
Select "New Printer"
Fill out whatever you want for Printer Name, Description, & Location
click "Forward"

Under "Select Connection" you should see "Lexmark Printer" and select that.
Next to it at "Enter Device URI" you should see the USB port where it is connected to ( such as - "z700:/dev/usblp0")
click "Forward"

You then have the option to "Select Printer From Database" or to "Provide PPD File". Choose "Provide PPD File"
Select the location "/usr/share/cups/model/Lexmark-Z700-lxz700cje-cups.ppd"

When you're done and back at the main Printer Configuration page, you should see listed under Local Printers "Z700-v1.0-1". That's a sign of success You can select it and change the options you want like making it your default printer, printing a test page, and so on, but that should pretty much do it.

I had tried many other ways and this was the only way that worked correctly for me. I hope it can be of help to some of you other p700 z700 owners.

---


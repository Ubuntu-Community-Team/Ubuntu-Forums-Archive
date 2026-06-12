---
title: "Problem with Magicolor 2400W printer"
date: 2009-03-18
forum: Hardware
---

### Post by spottraining on 2009-03-18
Hi

I get new printer. Konica-Minolta Magicolor 2400W. Before I check'd that there is some problems with this printer, but most people get it work with Ubuntu fine.

I installed the needed 2300w driver package and changed the printer as needed ( [https://bugs.launchpad.net/ubuntu/+source/m2300w/+bug/250583](https://bugs.launchpad.net/ubuntu/+source/m2300w/+bug/250583) )

But I have still problems. I am getting:  /usr/lib/cups/filter/foomatic-rip failed errors. I can't nothing to print, but I can print testpages at cups web frontend: [http://localhost:631](http://localhost:631)
But I need to work with this printer as usual printer. So any help is welcome to fix it. Right now I am not understanding, what can cause this error. From error log I see: Starting process "renderer" (generation 2) and this exiting with status 1 and how I understand, this and ca be one problematic place. But how to fix it?


Here is output of error log:
[HTML]D [18/Mar/2009:20:04:29 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:29 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:29 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:29 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:29 +0200] Get-Jobs ipp://localhost/jobs/
D [18/Mar/2009:20:04:29 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:29 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:29 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:29 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:29 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:29 +0200] Create-Printer-Subscription /
D [18/Mar/2009:20:04:29 +0200] cupsdCreateSubscription(con=0xb8635648(15), uri="/")
D [18/Mar/2009:20:04:29 +0200] pullmethod="ippget"
D [18/Mar/2009:20:04:29 +0200] notify-lease-duration=86400
D [18/Mar/2009:20:04:29 +0200] notify-time-interval=0
D [18/Mar/2009:20:04:29 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [18/Mar/2009:20:04:29 +0200] Added subscription 53 for server
I [18/Mar/2009:20:04:29 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:29 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:30 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:30 +0200] [Job 78] Unloading...
D [18/Mar/2009:20:04:31 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:31 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:31 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:31 +0200] Get-Notifications /
D [18/Mar/2009:20:04:31 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:31 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:31 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:36 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:36 +0200] cupsdReadClient: 15 POST /printers/magicolor-2400W HTTP/1.1
D [18/Mar/2009:20:04:36 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:36 +0200] Print-Job ipp://localhost/printers/magicolor-2400W
D [18/Mar/2009:20:04:36 +0200] add_job: requesting-user-name="suvi"
D [18/Mar/2009:20:04:36 +0200] Adding default job-sheets values "none,none"...
I [18/Mar/2009:20:04:36 +0200] [Job 79] Adding start banner page "none".
I [18/Mar/2009:20:04:36 +0200] Saving subscriptions.conf...
I [18/Mar/2009:20:04:36 +0200] [Job 79] Adding end banner page "none".
I [18/Mar/2009:20:04:36 +0200] [Job 79] File of type application/postscript queued by "suvi".
D [18/Mar/2009:20:04:36 +0200] [Job 79] hold_until=0
I [18/Mar/2009:20:04:36 +0200] [Job 79] Queued on "magicolor-2400W" by "suvi".
I [18/Mar/2009:20:04:36 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:36 +0200] [Job 79] job-sheets=none,none
D [18/Mar/2009:20:04:36 +0200] [Job 79] banner_page = 0
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[0]="magicolor-2400W"
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[1]="79"
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[2]="suvi"
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[3]="Test Page"
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[4]="1"
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[5]="job-uuid=urn:uuid:9cd03024-58d8-31e6-68b0-b7b3e6d9c8ea"
D [18/Mar/2009:20:04:36 +0200] [Job 79] argv[6]="/var/spool/cups/d00079-001"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[9]="SERVER_ADMIN=root@lapakas02"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[10]="SOFTWARE=CUPS/1.3.9"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[12]="TZ=Europe/Tallinn"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[13]="USER=root"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[16]="IPP_PORT=631"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[17]="CHARSET=utf-8"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[18]="LANG=et_EE.UTF8"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[19]="PPD=/etc/cups/ppd/magicolor-2400W.ppd"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[20]="RIP_MAX_CACHE=8m"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[21]="CONTENT_TYPE=application/postscript"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[22]="DEVICE_URI=usb://KONICA%20MINOLTA/magicolor%202400W"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[23]="PRINTER=magicolor-2400W"
D [18/Mar/2009:20:04:36 +0200] [Job 79] envp[24]="FINAL_CONTENT_TYPE=printer/magicolor-2400W"
I [18/Mar/2009:20:04:36 +0200] [Job 79] Started filter /usr/lib/cups/filter/pstopdf (PID 14313)
I [18/Mar/2009:20:04:36 +0200] [Job 79] Started filter /usr/lib/cups/filter/pdftopdf (PID 14314)
I [18/Mar/2009:20:04:36 +0200] [Job 79] Started filter /usr/lib/cups/filter/foomatic-rip (PID 14315)
I [18/Mar/2009:20:04:36 +0200] [Job 79] Started backend /usr/lib/cups/backend/usb (PID 14317)
I [18/Mar/2009:20:04:37 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] [Job 79] pstopdf argv[6] = 79 suvi Test Page 1 job-uuid=urn:uuid:9cd03024-58d8-31e6-68b0-b7b3e6d9c8ea /var/spool/cups/d00079-001
D [18/Mar/2009:20:04:37 +0200] [Job 79] PPD: /etc/cups/ppd/magicolor-2400W.ppd
D [18/Mar/2009:20:04:37 +0200] [Job 79] Getting input from file
D [18/Mar/2009:20:04:37 +0200] [Job 79] foomatic-rip version 4.0.0.195 running...
D [18/Mar/2009:20:04:37 +0200] [Job 79] Parsing PPD file ...
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option PrintoutMode
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option PageSize
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option ImageableArea
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option PaperDimension
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option MediaType
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option Resolution
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option Multipage
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option Debug
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option Quality
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option ColorMode
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option ColorProfile
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option DefRGB
D [18/Mar/2009:20:04:37 +0200] [Job 79] Added option Font
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] Parameter Summary
D [18/Mar/2009:20:04:37 +0200] [Job 79] -----------------
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] Spooler: cups
D [18/Mar/2009:20:04:37 +0200] [Job 79] Printer: magicolor-2400W
D [18/Mar/2009:20:04:37 +0200] [Job 79] Shell: /bin/bash
D [18/Mar/2009:20:04:37 +0200] [Job 79] PPD file: /etc/cups/ppd/magicolor-2400W.ppd
D [18/Mar/2009:20:04:37 +0200] [Job 79] ATTR file:
D [18/Mar/2009:20:04:37 +0200] [Job 79] Printer model: Minolta magicolor 2400W Foomatic/m2400w (recommended)
D [18/Mar/2009:20:04:37 +0200] [Job 79] Job title: Test Page
D [18/Mar/2009:20:04:37 +0200] [Job 79] File(s) to be printed:
D [18/Mar/2009:20:04:37 +0200] [Job 79] <STDIN>
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [18/Mar/2009:20:04:37 +0200] [Job 79] Pondering option 'job-uuid=urn:uuid:9cd03024-58d8-31e6-68b0-b7b3e6d9c8ea'
D [18/Mar/2009:20:04:37 +0200] [Job 79] Unknown option job-uuid=urn:uuid:9cd03024-58d8-31e6-68b0-b7b3e6d9c8ea.
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] ================================================
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] File: <STDIN>
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] ================================================
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] cupsdCloseClient: 15
I [18/Mar/2009:20:04:37 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:37 +0200] [Job 79] Printer using device file "/dev/usblp2"...
I [18/Mar/2009:20:04:37 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:37 +0200] [Job 79] backendRunLoop(print_fd=0, device_fd=5, use_bc=0, side_cb=0xb7faea80)
D [18/Mar/2009:20:04:37 +0200] [Job 79] Resolution: 1200x600
D [18/Mar/2009:20:04:37 +0200] [Job 79] Page size: A4
D [18/Mar/2009:20:04:37 +0200] [Job 79] Width: 595, height: 842, absolute margins: , , ,
D [18/Mar/2009:20:04:37 +0200] [Job 79] Relative margins: 11.3385826771654, 11.3385826771654, 11.338582677165, 11.338582677165
D [18/Mar/2009:20:04:37 +0200] [Job 79] PPD options: -r1200x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [18/Mar/2009:20:04:37 +0200] [Job 79] PostScript to be injected:
D [18/Mar/2009:20:04:37 +0200] [Job 79] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -r1200x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 - -
D [18/Mar/2009:20:04:37 +0200] [Job 79] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [18/Mar/2009:20:04:37 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:37 +0200] Get-Notifications /
D [18/Mar/2009:20:04:37 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:37 +0200] Get-Job-Attributes ipp://localhost/jobs/79
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:37 +0200] Get-Notifications /
D [18/Mar/2009:20:04:37 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Printers
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Classes
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Default
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:37 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:37 +0200] Get-Notifications /
D [18/Mar/2009:20:04:37 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] Get-Printer-Attributes ipp://localhost/printers/magicolor-2400W
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Printers
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Classes
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Default
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] Get-Printer-Attributes ipp://localhost/printers/magicolor-2400W
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Printers
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Classes
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] CUPS-Get-Default
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] [Job 79] Filetype: PDF
D [18/Mar/2009:20:04:37 +0200] [Job 79] Driver does not understand PDF input, converting to PostScript
D [18/Mar/2009:20:04:37 +0200] [Job 79] Starting process "pdf-to-ps" (generation 1)
D [18/Mar/2009:20:04:37 +0200] PID 14313 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [18/Mar/2009:20:04:37 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:37 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:37 +0200] Get-Printer-Attributes ipp://localhost/printers/magicolor-2400W
D [18/Mar/2009:20:04:37 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:37 +0200] cupsdCloseClient: 16
D [18/Mar/2009:20:04:37 +0200] PID 14314 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [18/Mar/2009:20:04:37 +0200] [Job 79] Filetype: PostScript
D [18/Mar/2009:20:04:37 +0200] [Job 79] Reading PostScript input ...
D [18/Mar/2009:20:04:37 +0200] [Job 79] --> This document is DSC-conforming!
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] -----------
D [18/Mar/2009:20:04:37 +0200] [Job 79] Found: %%BeginProlog
D [18/Mar/2009:20:04:37 +0200] [Job 79] Inserting option code into "Prolog" section.
D [18/Mar/2009:20:04:37 +0200] [Job 79] Found: %%EndProlog
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] -----------
D [18/Mar/2009:20:04:37 +0200] [Job 79] New page: %%Page: 1 1
D [18/Mar/2009:20:04:37 +0200] [Job 79] "Setup" section is missing, inserting it.
D [18/Mar/2009:20:04:37 +0200] [Job 79] Inserting PostScript code for CUPS' page accounting
D [18/Mar/2009:20:04:37 +0200] [Job 79] Inserting option code into "Setup" section.
D [18/Mar/2009:20:04:37 +0200] [Job 79]
D [18/Mar/2009:20:04:37 +0200] [Job 79] Found: %%BeginPageSetup
D [18/Mar/2009:20:04:37 +0200] [Job 79] Inserting option code into "PageSetup" section.
D [18/Mar/2009:20:04:38 +0200] [Job 79] Flushing FIFO.
D [18/Mar/2009:20:04:38 +0200] [Job 79]
D [18/Mar/2009:20:04:38 +0200] [Job 79] Starting renderer with command: "m2300w-wrapper -M 2400W -r 2 -p 4 -m 0 -o PrintoutMode=Auto   -o Quality=@PrintoutMode -o ColorMode=@PrintoutMode -o ColorProfile=@PrintoutMode -o DefaultRGB=sRGB  "
D [18/Mar/2009:20:04:38 +0200] [Job 79] Starting process "kid3" (generation 1)
D [18/Mar/2009:20:04:38 +0200] [Job 79] Starting process "kid4" (generation 2)
D [18/Mar/2009:20:04:38 +0200] [Job 79] JCL: %-12345X@PJL
D [18/Mar/2009:20:04:38 +0200] [Job 79] <job data>
D [18/Mar/2009:20:04:38 +0200] [Job 79]
D [18/Mar/2009:20:04:38 +0200] [Job 79] Starting process "renderer" (generation 2)
D [18/Mar/2009:20:04:38 +0200] [Job 79] renderer exited with status 1
D [18/Mar/2009:20:04:38 +0200] [Job 79] Possible error on renderer command line or PostScript error. Check options.DEBUG: Read 2914 bytes of print data...
D [18/Mar/2009:20:04:38 +0200] [Job 79]
D [18/Mar/2009:20:04:38 +0200] [Job 79] Closing renderer
D [18/Mar/2009:20:04:38 +0200] [Job 79] kid3 exited with status 3
D [18/Mar/2009:20:04:38 +0200] [Job 79] Process is dying with "Error closing renderer
D [18/Mar/2009:20:04:38 +0200] [Job 79] ", exit stat 3
D [18/Mar/2009:20:04:38 +0200] [Job 79] Cleaning up...
D [18/Mar/2009:20:04:38 +0200] [Job 79] Killing pdf-to-ps
I [18/Mar/2009:20:04:38 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:38 +0200] [Job 79] Wrote 2914 bytes of print data...
D [18/Mar/2009:20:04:38 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:38 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:38 +0200] Get-Notifications /
D [18/Mar/2009:20:04:38 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:38 +0200] Get-Notifications /
D [18/Mar/2009:20:04:38 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:38 +0200] CUPS-Get-Printers
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:38 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:38 +0200] Get-Notifications /
D [18/Mar/2009:20:04:38 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:38 +0200] CUPS-Get-Classes
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:38 +0200] CUPS-Get-Default
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:38 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:38 +0200] Get-Printer-Attributes ipp://localhost/printers/magicolor-2400W
D [18/Mar/2009:20:04:38 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:38 +0200] cupsdCloseClient: 16
D [18/Mar/2009:20:04:46 +0200] PID 14317 (/usr/lib/cups/backend/usb) exited with no errors.
E [18/Mar/2009:20:04:46 +0200] PID 14315 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
D [18/Mar/2009:20:04:46 +0200] [Job 79] File 0 is complete.
E [18/Mar/2009:20:04:46 +0200] [Job 79] Job stopped due to filter errors.
I [18/Mar/2009:20:04:46 +0200] Saving subscriptions.conf...
I [18/Mar/2009:20:04:46 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:46 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:46 +0200] Get-Notifications /
D [18/Mar/2009:20:04:46 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:46 +0200] CUPS-Get-Printers
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:46 +0200] CUPS-Get-Classes
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:46 +0200] Get-Notifications /
D [18/Mar/2009:20:04:46 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:46 +0200] CUPS-Get-Default
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdCloseClient: 16
D [18/Mar/2009:20:04:46 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:46 +0200] Get-Notifications /
D [18/Mar/2009:20:04:46 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdCloseClient: 16
D [18/Mar/2009:20:04:46 +0200] cupsdReadClient: 11 POST / HTTP/1.1
E [18/Mar/2009:20:04:46 +0200] cupsdAuthorize: Local authentication certificate not found!
D [18/Mar/2009:20:04:46 +0200] Get-Printer-Attributes ipp://localhost/printers/magicolor-2400W
D [18/Mar/2009:20:04:46 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:46 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:47 +0200] [Job 79] Unloading...
D [18/Mar/2009:20:04:51 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:51 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:51 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:51 +0200] Get-Job-Attributes ipp://localhost/jobs/79
D [18/Mar/2009:20:04:51 +0200] [Job 79] Loading attributes...
D [18/Mar/2009:20:04:51 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:51 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:51 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:51 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [18/Mar/2009:20:04:51 +0200] cupsdAuthorize: No authentication data provided.
D [18/Mar/2009:20:04:51 +0200] Cancel-Subscription /
D [18/Mar/2009:20:04:51 +0200] cupsdIsAuthorized: requesting-user-name="suvi"
I [18/Mar/2009:20:04:51 +0200] Saving subscriptions.conf...
D [18/Mar/2009:20:04:51 +0200] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [18/Mar/2009:20:04:51 +0200] cupsdCloseClient: 15
D [18/Mar/2009:20:04:51 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [18/Mar/2009:20:04:51 +0200] cupsdCloseClient: 14
D [18/Mar/2009:20:04:51 +0200] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [18/Mar/2009:20:04:51 +0200] cupsdAuthorize: No authentication data provided.[/HTML]

---

### Post by nbo10 on 2009-03-18
Check to make sure that it isn't just a ubuntu problem. I've had many general problems with magicolor printers.

---

### Post by spottraining on 2009-03-18
> **nbo10 said:**
> Check to make sure that it isn't just a ubuntu problem. I've had many general problems with magicolor printers.
You mean hardware problems?

But why I am getting then software error and why I can print testpages at Cups webfrontend?

---

### Post by spottraining on 2009-03-19
I filled bug report: [https://bugs.launchpad.net/ubuntu/+bug/345246](https://bugs.launchpad.net/ubuntu/+bug/345246)

But maybe some one has good idea, what to try?

---

### Post by spottraining on 2009-03-29
I upgraded now to Ubuntu 9.04 beta. In other computer the same printer with Jaunty - works fine.

But not in this Upgraded computer. Here is still the same problem. I removed foomatic and m2300w packages and installed them again - still the same situation.

So what settings can this cause? Some Gnome Printing settings?

I am still able to print testpages from cups webpage (localhost:631), but not other documents.

---


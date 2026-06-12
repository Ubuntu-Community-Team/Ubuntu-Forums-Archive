---
title: "Ubuntu can communicate with Deskjet 656c but not print"
date: 2010-09-05
forum: Hardware
---

### Post by Gogeden on 2010-09-05
I've been trying to get my mother's printer working under 10.04. She is using a HP Deskjet 656c. I have confirmed that the system can communicate with the printer. When a job is starting, the printer will feed in a sheet of paper, stop, wait, and then feed the paper back out again with nothing printed. That alone was a proof to me that the system and the printer are communicating. I checked my /var/log/cups/error_log file and here is what was stated:

E [05/Sep/2010:11:56:12 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [05/Sep/2010:14:49:23 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/Sep/2010:15:08:44 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
D [05/Sep/2010:15:15:52 -0400] [Job 11] The following messages were recorded from 15:12:51 to 15:15:52
D [05/Sep/2010:15:15:52 -0400] [Job 11] Adding start banner page "none".
D [05/Sep/2010:15:15:52 -0400] [Job 11] Adding end banner page "none".
D [05/Sep/2010:15:15:52 -0400] [Job 11] File of type application/postscript queued by "foxy".
D [05/Sep/2010:15:15:52 -0400] [Job 11] hold_until=0
D [05/Sep/2010:15:15:52 -0400] [Job 11] Queued on "DESKJET-656C" by "foxy".
D [05/Sep/2010:15:15:52 -0400] [Job 11] job-sheets=none,none
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[0]="DESKJET-656C"
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[1]="11"
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[2]="foxy"
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[3]="http://devils.nhl.com/club/scheduleprint.htm?season=20102011&gameType=2&team=NJD"
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[4]="1"
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[5]="Quality=FromPrintoutMode number-up=1 PrintoutMode=Normal PageSize=Letter job-uuid=urn:uuid:f411296e-597a-30ff-40dd-b2010f470aa6 job-originating-host-name=localhost"
D [05/Sep/2010:15:15:52 -0400] [Job 11] argv[6]="/var/spool/cups/d00011-001"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[8]="HOME=/var/spool/cups/tmp"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[10]="SERVER_ADMIN=root@foxy-desktop"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[11]="SOFTWARE=CUPS/1.4.3"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[13]="TZ=America/New_York"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[14]="USER=root"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[17]="IPP_PORT=631"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[18]="CHARSET=utf-8"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[19]="LANG=en_US.UTF-8"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[20]="PPD=/etc/cups/ppd/DESKJET-656C.ppd"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[21]="RIP_MAX_CACHE=256478k"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[22]="CONTENT_TYPE=application/postscript"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[23]="DEVICE_URI=hp:/usb/DESKJET_656C?serial=TH1AF1913T"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[24]="PRINTER_INFO=HEWLETT-PACKARD DESKJET 656C"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[25]="PRINTER_LOCATION=foxy-desktop"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[26]="PRINTER=DESKJET-656C"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[27]="CUPS_FILETYPE=document"
D [05/Sep/2010:15:15:52 -0400] [Job 11] envp[28]="FINAL_CONTENT_TYPE=printer/DESKJET-656C"
D [05/Sep/2010:15:15:52 -0400] [Job 11] Started filter /usr/lib/cups/filter/pstopdf (PID 1647)
D [05/Sep/2010:15:15:52 -0400] [Job 11] Started filter /usr/lib/cups/filter/pdftopdf (PID 1648)
D [05/Sep/2010:15:15:52 -0400] [Job 11] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1649)
D [05/Sep/2010:15:15:52 -0400] [Job 11] Started backend /usr/lib/cups/backend/hp (PID 1650)
D [05/Sep/2010:15:15:52 -0400] [Job 11] Getting input from file 
D [05/Sep/2010:15:15:52 -0400] [Job 11] pstopdf 6 args: 11 foxy [http://devils.nhl.com/club/scheduleprint.htm?season=20102011&gameType=2&team=NJD](http://devils.nhl.com/club/scheduleprint.htm?season=20102011&gameType=2&team=NJD) 1 Quality=FromPrintoutMode number-up=1 PrintoutMode=Normal PageSize=Letter job-uuid=urn:uuid:f411296e-597a-30ff-40dd-b2010f470aa6 job-originating-host-name=localhost /var/spool/cups/d00011-001
D [05/Sep/2010:15:15:52 -0400] [Job 11] PPD: /etc/cups/ppd/DESKJET-656C.ppd
D [05/Sep/2010:15:15:52 -0400] [Job 11] foomatic-rip version 4.0.4.217 running...
D [05/Sep/2010:15:15:52 -0400] [Job 11] Parsing PPD file ...
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option Resolution
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option PageSize
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option Model
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option PrintoutMode
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option Quality
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option ImageableArea
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option PaperDimension
D [05/Sep/2010:15:15:52 -0400] [Job 11] Added option Font
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Parameter Summary
D [05/Sep/2010:15:15:52 -0400] [Job 11] -----------------
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Spooler: cups
D [05/Sep/2010:15:15:52 -0400] [Job 11] Printer: DESKJET-656C
D [05/Sep/2010:15:15:52 -0400] [Job 11] Shell: /bin/bash
D [05/Sep/2010:15:15:52 -0400] [Job 11] PPD file: /etc/cups/ppd/DESKJET-656C.ppd
D [05/Sep/2010:15:15:52 -0400] [Job 11] ATTR file: 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Printer model: HP Deskjet 656c hpijs, 3.10.2
D [05/Sep/2010:15:15:52 -0400] [Job 11] Job title: [http://devils.nhl.com/club/scheduleprint.htmseason=20102011gameType=2team=NJD](http://devils.nhl.com/club/scheduleprint.htmseason=20102011gameType=2team=NJD)
D [05/Sep/2010:15:15:52 -0400] [Job 11] File(s) to be printed:
D [05/Sep/2010:15:15:52 -0400] [Job 11] <STDIN>
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [05/Sep/2010:15:15:52 -0400] [Job 11] Printing system options:
D [05/Sep/2010:15:15:52 -0400] [Job 11] Pondering option 'number-up=1'
D [05/Sep/2010:15:15:52 -0400] [Job 11] Unknown option number-up=1.
D [05/Sep/2010:15:15:52 -0400] [Job 11] Pondering option 'job-uuid=urn:uuid:f411296e-597a-30ff-40dd-b2010f470aa6'
D [05/Sep/2010:15:15:52 -0400] [Job 11] Unknown option job-uuid=urn:uuid:f411296e-597a-30ff-40dd-b2010f470aa6.
D [05/Sep/2010:15:15:52 -0400] [Job 11] Pondering option 'job-originating-host-name=localhost'
D [05/Sep/2010:15:15:52 -0400] [Job 11] Unknown option job-originating-host-name=localhost.
D [05/Sep/2010:15:15:52 -0400] [Job 11] Options from the PPD file:
D [05/Sep/2010:15:15:52 -0400] [Job 11] Pondering option 'Quality=FromPrintoutMode'
D [05/Sep/2010:15:15:52 -0400] [Job 11] Pondering option 'PrintoutMode=Normal'
D [05/Sep/2010:15:15:52 -0400] [Job 11] Pondering option 'PageSize=Letter'
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] ================================================
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] File: <STDIN>
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] ================================================
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Resolution: 300
D [05/Sep/2010:15:15:52 -0400] [Job 11] Page size: Letter
D [05/Sep/2010:15:15:52 -0400] [Job 11] Width: 612, height: 792, absolute margins: 18, 48.240001678467, 594, 783
D [05/Sep/2010:15:15:52 -0400] [Job 11] Relative margins: 18, 48.240001678467, 18, 9
D [05/Sep/2010:15:15:52 -0400] [Job 11] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [05/Sep/2010:15:15:52 -0400] [Job 11] PostScript to be injected: 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [05/Sep/2010:15:15:52 -0400] [Job 11] Filetype: PDF
D [05/Sep/2010:15:15:52 -0400] [Job 11] Storing temporary files in /var/spool/cups/tmp
D [05/Sep/2010:15:15:52 -0400] [Job 11] File contains 2 pages
D [05/Sep/2010:15:15:52 -0400] [Job 11] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="DESKJET 630" -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-AzGASz 
D [05/Sep/2010:15:15:52 -0400] [Job 11] Starting process "kid3" (generation 1)
D [05/Sep/2010:15:15:52 -0400] [Job 11] Starting process "kid4" (generation 2)
D [05/Sep/2010:15:15:52 -0400] [Job 11] Starting process "renderer" (generation 2)
D [05/Sep/2010:15:15:52 -0400] [Job 11] JCL: %-12345X@PJL
D [05/Sep/2010:15:15:52 -0400] [Job 11] <job data> 
D [05/Sep/2010:15:15:52 -0400] [Job 11] 
D [05/Sep/2010:15:15:52 -0400] [Job 11] STATE: +connecting-to-device
D [05/Sep/2010:15:15:52 -0400] [Job 11] STATE: -connecting-to-device
D [05/Sep/2010:15:15:52 -0400] [Job 11] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [05/Sep/2010:15:15:52 -0400] [Job 11] prnt/backend/hp.c 625: ERROR: 5021 device communication error!
D [05/Sep/2010:15:15:52 -0400] [Job 11] GPL Ghostscript 8.71: Unrecoverable error, exit code 1
D [05/Sep/2010:15:15:52 -0400] [Job 11] Job stopped due to printer being paused.
D [05/Sep/2010:15:15:52 -0400] [Job 11] Process is dying with "Caught termination signal: Job canceled
D [05/Sep/2010:15:15:52 -0400] [Job 11] ", exit stat 0
D [05/Sep/2010:15:15:52 -0400] [Job 11] Cleaning up...
D [05/Sep/2010:15:15:52 -0400] [Job 11] Killing kid3
D [05/Sep/2010:15:15:52 -0400] [Job 11] Process is dying with "Caught termination signal: Job canceled
D [05/Sep/2010:15:15:52 -0400] [Job 11] ", exit stat 0
D [05/Sep/2010:15:15:52 -0400] [Job 11] Cleaning up...
D [05/Sep/2010:15:15:52 -0400] [Job 11] Killing kid4
D [05/Sep/2010:15:15:52 -0400] [Job 11] Killing renderer
D [05/Sep/2010:15:15:52 -0400] [Job 11] Backend returned status 4 (stop printer)
D [05/Sep/2010:15:15:52 -0400] [Job 11] End of messages
D [05/Sep/2010:15:15:52 -0400] [Job 11] printer-state=5(stopped)
D [05/Sep/2010:15:15:52 -0400] [Job 11] printer-state-message="Unplugged or turned off"
D [05/Sep/2010:15:15:52 -0400] [Job 11] printer-state-reasons=paused
E [05/Sep/2010:15:16:31 -0400] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost/printers/DESKJET-656C) from localhost
E [05/Sep/2010:15:38:35 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!

I canceled the jobs a few times because I knew from fact that they were not going to finish printing. I installed the HPLIP Manager. Not a difference in printing ability. From close examination of the log above, there is a backend error. I noticed after awhile from fiddling with the printer that the CPU usage was at 100%. I opened a bash terminal and used top which stated that backend was the culprit of the high CPU usage.

Interesting, eh?


Thank you in advance :) :lol:

---


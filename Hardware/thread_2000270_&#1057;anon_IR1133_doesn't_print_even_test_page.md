---
title: "&#1057;anon IR1133 doesn't print even test page"
date: 2012-06-09
forum: Hardware
---

### Post by justheard on 2012-06-09
Hi All!
Worn out with the installation of MFP Canon IR 1133 under Ubuntu 10.04
That I did not react MFP, even test print in CUPS does not work, all of which is lost or put in queue.
The description of the using driver [http://software.canon-europe.com/software/0042553.asp?model](http://software.canon-europe.com/software/0042553.asp?model) =
   is written that we must have CUPS and foomatic. 
But In the package manager it seems what cups and foomatic are installed, except  foomatic - gui, - it cann't be installed cause an error occurs in the process that says it cann't be installed cause foomatic-gui depends of phyton-gtkhtml2 which is not in package manager and havent been installed yet.
There is an error occurs when trying to add printer by adding ppd.tz(in the installation directory) -  CUPS server internal error, but when trying to add *.ppd not from the installation directory printer is added but is silent.
All attempts communication with the printer - an attempt to test print, then do not even try.
Part of the error log:
E [09/Jun/2012:00:57:41 +0400] [CGI] Unable to scan "@LOCAL"!
E [09/Jun/2012:01:00:02 +0400] [CGI] Unable to scan "@LOCAL"!
E [09/Jun/2012:01:02:12 +0400] [CGI] Unable to scan "@LOCAL"!
D [09/Jun/2012:01:15:31 +0400] [Job 125] The following messages were recorded from 01:15:18 to 01:15:31
D [09/Jun/2012:01:15:31 +0400] [Job 125] Job submission timed out.
D [09/Jun/2012:01:15:31 +0400] [Job 125] job-sheets=none,none
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[0]="Canon-imageRUNNER1133-series"
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[1]="125"
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[2]="anonymous"
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[3]="Test Page"
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[4]="1"
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[5]="job-uuid=urn:uuid:22d60eec-32b5-3445-7c67-2d0601656ed1 job-originating-host-name=localhost"
D [09/Jun/2012:01:15:31 +0400] [Job 125] argv[6]="/var/spool/cups/d00125-001"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[8]="HOME=/var/spool/cups/tmp"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[10]="SERVER_ADMIN=root@kom-desktop"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[11]="SOFTWARE=CUPS/1.4.3"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[13]="TZ=Europe/Moscow"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[14]="USER=root"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[17]="IPP_PORT=631"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[18]="CHARSET=utf-8"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[19]="LANG=en_US.UTF-8"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[20]="PPD=/etc/cups/ppd/Canon-imageRUNNER1133-series.ppd"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[21]="RIP_MAX_CACHE=254205k"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[23]="DEVICE_URI=dnssd://Canon%20imageRUNNER1133%20series._pdl-datastream._tcp.local/"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[24]="PRINTER_INFO=Canon imageRUNNER1133 series"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[25]="PRINTER_LOCATION="
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[26]="PRINTER=Canon-imageRUNNER1133-series"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[27]="CUPS_FILETYPE=document"
D [09/Jun/2012:01:15:31 +0400] [Job 125] envp[28]="FINAL_CONTENT_TYPE=printer/Canon-imageRUNNER1133-series"
D [09/Jun/2012:01:15:31 +0400] [Job 125] Started filter /usr/lib/cups/filter/bannertops (PID 3296)
D [09/Jun/2012:01:15:31 +0400] [Job 125] Started filter /usr/lib/cups/filter/pstopdf (PID 3297)
D [09/Jun/2012:01:15:31 +0400] [Job 125] Started filter /usr/lib/cups/filter/pdftopdf (PID 3298)
D [09/Jun/2012:01:15:31 +0400] [Job 125] Started filter /usr/lib/cups/filter/foomatic-rip (PID 3299)
D [09/Jun/2012:01:15:31 +0400] [Job 125] Started backend /usr/lib/cups/backend/dnssd (PID 3300)
D [09/Jun/2012:01:15:31 +0400] [Job 125] Getting input from file 
D [09/Jun/2012:01:15:31 +0400] [Job 125] pstopdf 5 args: 125 anonymous Test Page 1 job-uuid=urn:uuid:22d60eec-32b5-3445-7c67-2d0601656ed1 job-originating-host-name=localhost
D [09/Jun/2012:01:15:31 +0400] [Job 125] PPD: /etc/cups/ppd/Canon-imageRUNNER1133-series.ppd
D [09/Jun/2012:01:15:31 +0400] [Job 125] load_banner(filename="/var/spool/cups/d00125-001")
D [09/Jun/2012:01:15:31 +0400] [Job 125] foomatic-rip version 4.0.4.217 running...
D [09/Jun/2012:01:15:31 +0400] [Job 125] Parsing PPD file ...
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option OptCST
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option PrintDensity
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option WideA4
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option CNResolution
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option Resolution
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option GSResolution
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option JCLResolution
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option InputSlot
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option MediaType
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option Duplex
D [09/Jun/2012:01:15:31 +0400] [Job 125] Resolving "Canon imageRUNNER1133 series._pdl-datastream._tcp.local"...
D [09/Jun/2012:01:15:31 +0400] [Job 125] STATE: +connecting-to-device
D [09/Jun/2012:01:15:31 +0400] [Job 125] Resolving "Canon imageRUNNER1133 series", regtype="_pdl-datastream._tcp", domain="local."...
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option BindingLocation
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option TonerSave
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option ScreenProc
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option Transfer
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option PageSize
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option ImageableArea
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option PaperDimension
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option Font
D [09/Jun/2012:01:15:31 +0400] [Job 125] Added option ColorSep
D [09/Jun/2012:01:15:31 +0400] [Job 125] 
D [09/Jun/2012:01:15:31 +0400] [Job 125] Parameter Summary
D [09/Jun/2012:01:15:31 +0400] [Job 125] -----------------
D [09/Jun/2012:01:15:31 +0400] [Job 125] 
D [09/Jun/2012:01:15:31 +0400] [Job 125] Spooler: cups
D [09/Jun/2012:01:15:31 +0400] [Job 125] Printer: Canon-imageRUNNER1133-series
D [09/Jun/2012:01:15:31 +0400] [Job 125] Shell: /bin/bash
D [09/Jun/2012:01:15:31 +0400] [Job 125] PPD file: /etc/cups/ppd/Canon-imageRUNNER1133-series.ppd
D [09/Jun/2012:01:15:31 +0400] [Job 125] ATTR file: 
D [09/Jun/2012:01:15:31 +0400] [Job 125] Printer model: Canon iR1133 PCL
D [09/Jun/2012:01:15:31 +0400] [Job 125] Job title: Test Page
D [09/Jun/2012:01:15:31 +0400] [Job 125] File(s) to be printed:
D [09/Jun/2012:01:15:31 +0400] [Job 125] <STDIN>
D [09/Jun/2012:01:15:31 +0400] [Job 125] 
D [09/Jun/2012:01:15:31 +0400] [Job 125] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [09/Jun/2012:01:15:31 +0400] [Job 125] Printing system options:
D [09/Jun/2012:01:15:31 +0400] [Job 125] Pondering option 'job-uuid=urn:uuid:22d60eec-32b5-3445-7c67-2d0601656ed1'
D [09/Jun/2012:01:15:31 +0400] [Job 125] Unknown option job-uuid=urn:uuid:22d60eec-32b5-3445-7c67-2d0601656ed1.
D [09/Jun/2012:01:15:31 +0400] [Job 125] Pondering option 'job-originating-host-name=localhost'
D [09/Jun/2012:01:15:31 +0400] [Job 125] Unknown option job-originating-host-name=localhost.
D [09/Jun/2012:01:15:31 +0400] [Job 125] Options from the PPD file:
D [09/Jun/2012:01:15:31 +0400] [Job 125]  

Please suggest what is missing this driver?:

*PPD-Adobe: "4.3"
*% Copyright 2011 SIC International. All rights reserved.
*% CQue version: 2.0-2.
*% Foomatic target: PCL5.
*% Canon PostScript(R) Printer Description File
*% Release version 3.10 2011
*%
*FormatVersion: "4.3"
*FileVersion: "1.0"
*LanguageEncoding: ISOLatin1
*LanguageVersion: English
*Manufacturer: "Canon"
*PCFileName: "CEIR1133.PPD"
*Product: "(CNimageRUNNER1133 series)"
*PSVersion: "(3015.100)1"
*ModelName: "Canon iR1133 PCL"
*ShortNickName: "Canon iR1133 PCL"
*NickName: "Canon iR1133 PCL"
*%
*cupsVersion:      1.1
*cupsManualCopies: True
*cupsModelNumber:  2
*cupsFilter:       "application/vnd.cups-postscript 100 foomatic-rip"
*cupsFilter:       "application/vnd.cups-pdf 0 foomatic-rip"
*cupsFilter:       "application/vnd.apple-pdf 25 foomatic-rip"
*%
*OpenGroup: InstallableOptions/Attached Options
*%
*OpenUI *OptCST/250 Sheet Cassette: Boolean
*DefaultOptCST: False
*OptCST False/Off: ""
*OptCST True/On: ""
*CloseUI: *OptCST
*%
*CloseGroup: InstallableOptions
*%
*%
*%========== Ghostscript Command line ==========
*%
*FoomaticIDs: Canon pxlmono
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dPDFFitPage  -sDEVICE=ljet4 -dNOPAUSE %B%A%C -sOutputFile=- - %D%E | sicgsfilter -MPCL -NP %G%H%I -u&user; -V&quot;&title;&quot; -n&copies; "
*%
*%
*UIConstraints: *InputSlot Tray2 *OptCST False
*UIConstraints: *OptCST False *InputSlot Tray2
*%
*UIConstraints: *InputSlot Tray1 *PageSize Monarch
*UIConstraints: *PageSize Monarch *InputSlot Tray1 

Also I ran cque from command line (supposedly out of the way of installation), created and find the printer, but all the same....
Please help in this matter because all of my guesses freshman ended, nothing happens, the test print does not :(print ....

---

### Post by justheard on 2012-06-10
I localized the problem and think that the problem in two things:
- [CGI] Unable to scan "@LOCAL"
- Returning IPP client-error-document-format-not-supported for Send-Document (ipp://localhost:631/printers/Canon_iR1133_UFRII_LT) from localhost
Maybe somebody can say something about this:(

---


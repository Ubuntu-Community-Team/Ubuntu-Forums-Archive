---
title: "HP 712C Problems"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by BatteryCell on 2006-07-02
My printer worked in Breezy if I started lo (ifconfig lo up) then restarted networking and cupsys (/etc/init.d/networking restart ...), alas it does not work in Dapper.  My printer is recognized, can be sent a page to print, and it says (in localhost:631) that all the jobs that i started were finished, but nothing actually prints.
Here is my /var/log/cups/error_log when I try to print a job:
```

D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 6 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] CUPS-Get-Printers
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdAcceptClient: 7 from localhost:631 (IPv4)
D [02/Jul/2006:11:12:57 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 7 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] CUPS-Get-Printers
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdCloseClient: 7
D [02/Jul/2006:11:12:57 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 6 POST /classes/ HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] CUPS-Get-Classes
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdAcceptClient: 8 from localhost:631 (IPv4)
D [02/Jul/2006:11:12:57 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 8 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] CUPS-Get-Default
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdCloseClient: 8
D [02/Jul/2006:11:12:57 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 6 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] Get-Printer-Attributes ipp://kubuntu:631/printers/MyPrinter
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdAcceptClient: 8 from localhost:631 (IPv4)
D [02/Jul/2006:11:12:57 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] Get-Printer-Attributes ipp://localhost/printers/MyPrinter
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 8 GET /printers/MyPrinter.ppd HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] write_file: 8 file=6
D [02/Jul/2006:11:12:57 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:12:57 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [02/Jul/2006:11:12:57 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:12:57 -0400] Get-Jobs ipp://kubuntu:631/printers/MyPrinter
D [02/Jul/2006:11:12:57 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:12:57 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:00 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [02/Jul/2006:11:13:00 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:00 -0400] Get-Printer-Attributes ipp://localhost/printers/MyPrinter
D [02/Jul/2006:11:13:00 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:00 -0400] cupsdReadClient: 8 GET /printers/MyPrinter.ppd HTTP/1.1
D [02/Jul/2006:11:13:00 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:00 -0400] write_file: 8 file=6
D [02/Jul/2006:11:13:00 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:00 -0400] cupsdReadClient: 6 POST /printers/MyPrinter HTTP/1.1
D [02/Jul/2006:11:13:00 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:00 -0400] Print-Job ipp://localhost/printers/MyPrinter
D [02/Jul/2006:11:13:00 -0400] print_job: auto-typing file...
D [02/Jul/2006:11:13:00 -0400] print_job: request file type is application/postscript.
D [02/Jul/2006:11:13:00 -0400] add_job: requesting-user-name="root"
D [02/Jul/2006:11:13:00 -0400] Adding default job-sheets values "none,none"...
I [02/Jul/2006:11:13:00 -0400] Adding start banner page "none" to job 230.
D [02/Jul/2006:11:13:00 -0400] Discarding unused job-created event...
I [02/Jul/2006:11:13:00 -0400] Job 230 queued on "MyPrinter" by "root".
D [02/Jul/2006:11:13:00 -0400] Job 230 hold_until = 0
D [02/Jul/2006:11:13:00 -0400] Discarding unused printer-state-changed event...
D [02/Jul/2006:11:13:00 -0400] job-sheets=none,none
D [02/Jul/2006:11:13:00 -0400] banner_page = 0
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[0]="MyPrinter"
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[1]="230"
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[2]="root"
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[3]="KDE Print Test"
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[4]="1"
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[5]="multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3 job-uuid=urn:uuid:f4be85dc-0d1c-39bc-6bf5-428a280e3d76"
D [02/Jul/2006:11:13:00 -0400] [Job 230] argv[6]="/var/spool/cups/d00230-001"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[9]="SERVER_ADMIN=root@kubuntu"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[10]="SOFTWARE=CUPS/1.2.0"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[12]="TZ=America/New_York"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[13]="USER=root"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[16]="IPP_PORT=631"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[17]="CHARSET=utf-8"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[18]="LANG=en_US"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[19]="PPD=/etc/cups/ppd/MyPrinter.ppd"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[20]="RIP_MAX_CACHE=8m"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[21]="CONTENT_TYPE=application/postscript"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[22]="DEVICE_URI=parallel:/dev/lp0"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[23]="PRINTER=MyPrinter"
D [02/Jul/2006:11:13:00 -0400] [Job 230] envp[24]="FINAL_CONTENT_TYPE=printer/MyPrinter"
I [02/Jul/2006:11:13:00 -0400] Started filter /usr/lib/cups/filter/pstops (PID 11360) for job 230.
I [02/Jul/2006:11:13:00 -0400] Started filter /usr/lib/cups/filter/foomatic-rip (PID 11361) for job 230.
I [02/Jul/2006:11:13:00 -0400] Started backend /usr/lib/cups/backend/parallel (PID 11362) for job 230.
D [02/Jul/2006:11:13:00 -0400] Discarding unused job-state event...
D [02/Jul/2006:11:13:00 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:00 -0400] [Job 230] Page = 612x792; 0,0 to 612,792
D [02/Jul/2006:11:13:00 -0400] [Job 230] slow_collate=0, slow_duplex=0, slow_order=0
D [02/Jul/2006:11:13:00 -0400] [Job 230] Before copy_comments - %!PS-Adobe-3.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] %!PS-Adobe-3.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%BoundingBox: 0 0 612 792
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%Pages: 1
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%LanguageLevel: 1
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%DocumentData: Clean7Bit
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%DocumentSuppliedResources: procset testprint/1.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%DocumentNeededResources: font Helvetica Helvetica-Bold Times-Roman
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%Creator: Michael Sweet, Easy Software Products
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%CreationDate: May 11, 1999
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%Title: Test Page
D [02/Jul/2006:11:13:00 -0400] [Job 230] %%EndComments
D [02/Jul/2006:11:13:00 -0400] [Job 230] Before copy_prolog - %%BeginProlog
D [02/Jul/2006:11:13:00 -0400] [Job 230] Before copy_setup - %%Page: 1 1
D [02/Jul/2006:11:13:00 -0400] [Job 230] Before page loop - %%Page: 1 1
D [02/Jul/2006:11:13:00 -0400] [Job 230] Copying page 1...
D [02/Jul/2006:11:13:00 -0400] [Job 230] pagew = 612.0, pagel = 792.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] bboxw = 612, bboxl = 792
D [02/Jul/2006:11:13:00 -0400] [Job 230] PageLeft = 0.0, PageRight = 612.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] PageTop = 792.0, PageBottom = 0.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] PageWidth = 612.0, PageLength = 792.0
D [02/Jul/2006:11:13:00 -0400] [Job 230] Wrote 1 pages...
D [02/Jul/2006:11:13:00 -0400] [Job 230] perl: warning: Setting locale failed.
D [02/Jul/2006:11:13:00 -0400] [Job 230] perl: warning: Please check that your locale settings:
D [02/Jul/2006:11:13:00 -0400] [Job 230] LANGUAGE = (unset),
D [02/Jul/2006:11:13:00 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:00 -0400] PID 11360 (/usr/lib/cups/filter/pstops) exited with no errors.
D [02/Jul/2006:11:13:00 -0400] [Job 230] LC_ALL = (unset),
D [02/Jul/2006:11:13:00 -0400] [Job 230] LANG = "en_US"
D [02/Jul/2006:11:13:00 -0400] [Job 230] are supported and installed on your system.
D [02/Jul/2006:11:13:00 -0400] [Job 230] perl: warning: Falling back to the standard locale ("C").
D [02/Jul/2006:11:13:00 -0400] [Job 230] LPGETSTATUS returned a port status of 5E...
D [02/Jul/2006:11:13:00 -0400] [Job 230] foomatic-rip version $Revision: 3.43.2.15 $ running...
D [02/Jul/2006:11:13:00 -0400] [Job 230] Parsing PPD file ...
D [02/Jul/2006:11:13:00 -0400] [Job 230] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option ColorSpace
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option Resolution
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option PageSize
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option PageRegion
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option ImageableArea
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option PaperDimension
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option EconoFast
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option ColorMode
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option Dither
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option Bidirectional
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option Blackness
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option BottomMargin
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option LeftMargin
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option RightMargin
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option TopMargin
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option XOffset
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option YOffset
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option Model
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option GammaFile
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option pnmFormat
D [02/Jul/2006:11:13:00 -0400] [Job 230] Added option Font
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] Parameter Summary
D [02/Jul/2006:11:13:00 -0400] [Job 230] -----------------
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] Spooler: cups
D [02/Jul/2006:11:13:00 -0400] [Job 230] Printer: MyPrinter
D [02/Jul/2006:11:13:00 -0400] [Job 230] PPD file: /etc/cups/ppd/MyPrinter.ppd
D [02/Jul/2006:11:13:00 -0400] [Job 230] Printer model: HP DeskJet 712C Foomatic/pnm2ppa (recommended)
D [02/Jul/2006:11:13:00 -0400] [Job 230] Job title: KDE Print Test
D [02/Jul/2006:11:13:00 -0400] [Job 230] File(s) to be printed: 
D [02/Jul/2006:11:13:00 -0400] [Job 230] <STDIN>
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [02/Jul/2006:11:13:00 -0400] [Job 230] Pondering option 'multiple-document-handling=separate-documents-uncollated-copies'
D [02/Jul/2006:11:13:00 -0400] [Job 230] Unknown option multiple-document-handling=separate-documents-uncollated-copies.
D [02/Jul/2006:11:13:00 -0400] [Job 230] Pondering option 'orientation-requested=3'
D [02/Jul/2006:11:13:00 -0400] [Job 230] Unknown option orientation-requested=3.
D [02/Jul/2006:11:13:00 -0400] [Job 230] Pondering option 'job-uuid=urn:uuid:f4be85dc-0d1c-39bc-6bf5-428a280e3d76'
D [02/Jul/2006:11:13:00 -0400] [Job 230] Unknown option job-uuid=urn:uuid:f4be85dc-0d1c-39bc-6bf5-428a280e3d76.
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] ================================================
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] File: <STDIN>
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] ================================================
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] Reading PostScript input ...
D [02/Jul/2006:11:13:00 -0400] [Job 230] --> This document is DSC-conforming!
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] -----------
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginProlog
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%EndProlog
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] -----------
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginSetup
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *PageSize Letter
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: PageSize=Letter --> Option will be set by PostScript interpreter
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *pnmFormat PixMap
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: pnmFormat=PixMap --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: pnmFormat=PixMap
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: pnmFormat=PixMap --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *ColorMode CMYK
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: ColorMode=CMYK --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: ColorMode=CMYK
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: ColorMode=CMYK --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *EconoFast Off
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: EconoFast=Off --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: EconoFast=Off
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: EconoFast=Off --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *Dither FloydSteinberg
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: Dither=FloydSteinberg --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: Dither=FloydSteinberg
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: Dither=FloydSteinberg --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *GammaFile Default
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: GammaFile=Default --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: GammaFile=Default
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: GammaFile=Default --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *Bidirectional Default
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: Bidirectional=Default --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: Bidirectional=Default
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: Bidirectional=Default --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *Blackness 2
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: Blackness=2 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: Blackness=2
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: Blackness=2 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *TopMargin 10
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: TopMargin=10 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: TopMargin=10
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: TopMargin=10 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *BottomMargin 150
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: BottomMargin=150 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: BottomMargin=150
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: BottomMargin=150 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *LeftMargin 10
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: LeftMargin=10 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: LeftMargin=10
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: LeftMargin=10 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *RightMargin 10
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: RightMargin=10 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: RightMargin=10
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: RightMargin=10 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *XOffset 160
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: XOffset=160 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: XOffset=160
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: XOffset=160 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginFeature: *YOffset 50
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: YOffset=50 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %% FoomaticRIPOptionSetting: YOffset=50
D [02/Jul/2006:11:13:00 -0400] [Job 230] Option: YOffset=50 --> Setting option
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%EndSetup
D [02/Jul/2006:11:13:00 -0400] [Job 230] Inserting PostScript code for CUPS' page accounting
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] -----------
D [02/Jul/2006:11:13:00 -0400] [Job 230] New page:  1 1
D [02/Jul/2006:11:13:00 -0400] [Job 230] Inserting option code into "PageSetup" section.
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%BeginPageSetup
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found: %%EndPageSetup
D [02/Jul/2006:11:13:00 -0400] [Job 230] End of page header
D [02/Jul/2006:11:13:00 -0400] [Job 230] Stopping search for page header options
D [02/Jul/2006:11:13:00 -0400] [Job 230] Found:
D [02/Jul/2006:11:13:00 -0400] [Job 230] (x) show				% "x"
D [02/Jul/2006:11:13:00 -0400] [Job 230] --> Output goes directly to the renderer now.
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] Starting renderer
D [02/Jul/2006:11:13:00 -0400] [Job 230] JCL: <job data> 
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] renderer PID kid4=11365
D [02/Jul/2006:11:13:00 -0400] [Job 230] renderer command: gs -q -dNOPAUSE -dPARANOIDSAFER -dBATCH -r600 -sDEVICE=ppmraw  -sOutputFile=- - | pnm2ppa -v 712  -B 2 -t 10 -b 150 -l 10 -r 10 -x 160 -y 50 -i - -o -
D [02/Jul/2006:11:13:00 -0400] [Job 230] 
D [02/Jul/2006:11:13:00 -0400] [Job 230] Closing renderer
D [02/Jul/2006:11:13:00 -0400] [Job 230] perl: warning: Setting locale failed.
D [02/Jul/2006:11:13:00 -0400] [Job 230] perl: warning: Please check that your locale settings:
D [02/Jul/2006:11:13:00 -0400] [Job 230] LANGUAGE = (unset),
D [02/Jul/2006:11:13:00 -0400] [Job 230] LC_ALL = (unset),
D [02/Jul/2006:11:13:00 -0400] [Job 230] LANG = "en_US"
D [02/Jul/2006:11:13:00 -0400] [Job 230] are supported and installed on your system.
D [02/Jul/2006:11:13:00 -0400] [Job 230] perl: warning: Falling back to the standard locale ("C").
D [02/Jul/2006:11:13:01 -0400] [Job 230] foomatic-gswrapper: gs '-dNOPAUSE' '-dPARANOIDSAFER' '-dBATCH' '-r600' '-sDEVICE=ppmraw' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [02/Jul/2006:11:13:01 -0400] [Job 230] ESP Ghostscript 815.02 (2006-04-19)
D [02/Jul/2006:11:13:01 -0400] [Job 230] Copyright (C) 2004 artofcode LLC, Benicia, CA.  All rights reserved.
D [02/Jul/2006:11:13:01 -0400] [Job 230] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [02/Jul/2006:11:13:01 -0400] [Job 230] Loading NimbusSanL-Bold font from /var/lib/defoma/gs.d/dirs/fonts/n019004l.pfb... 2949456 1520019 1719744 426661 1 done.
D [02/Jul/2006:11:13:01 -0400] [Job 230] Loading NimbusSanL-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n019003l.pfb... 2982736 1619145 1719744 427521 1 done.
D [02/Jul/2006:11:13:01 -0400] [Job 230] Loading NimbusRomNo9L-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n021003l.pfb... 3084456 1781470 1719744 428941 1 done.
D [02/Jul/2006:11:13:01 -0400] [Job 230] Loading NimbusSanL-BoldItal font from /var/lib/defoma/gs.d/dirs/fonts/n019024l.pfb... 3218656 1909961 1739928 447613 1 done.
D [02/Jul/2006:11:13:01 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 6 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] CUPS-Get-Printers
D [02/Jul/2006:11:13:01 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:01 -0400] cupsdAcceptClient: 9 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:01 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 9 POST /classes/ HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] CUPS-Get-Classes
D [02/Jul/2006:11:13:01 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:01 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:01 -0400] cupsdCloseClient: 9
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 6 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] CUPS-Get-Default
D [02/Jul/2006:11:13:01 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:01 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:01 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 6 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] Get-Printer-Attributes ipp://kubuntu:631/printers/MyPrinter
D [02/Jul/2006:11:13:01 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] Get-Printer-Attributes ipp://localhost/printers/MyPrinter
D [02/Jul/2006:11:13:01 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:01 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 8 GET /printers/MyPrinter.ppd HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] write_file: 8 file=6
D [02/Jul/2006:11:13:01 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:01 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [02/Jul/2006:11:13:01 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:01 -0400] Get-Jobs ipp://kubuntu:631/printers/MyPrinter
D [02/Jul/2006:11:13:01 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:01 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:05 -0400] [Job 230] KID3 exited with status 0
D [02/Jul/2006:11:13:05 -0400] [Job 230] tail process done writing data to STDOUT
D [02/Jul/2006:11:13:05 -0400] [Job 230] KID4 exited with status 0
D [02/Jul/2006:11:13:05 -0400] [Job 230] Renderer exit stat: 0
D [02/Jul/2006:11:13:05 -0400] [Job 230] KID4 finished
D [02/Jul/2006:11:13:05 -0400] [Job 230] KID3 finished
D [02/Jul/2006:11:13:05 -0400] [Job 230] Renderer process finished
D [02/Jul/2006:11:13:05 -0400] [Job 230] 
D [02/Jul/2006:11:13:05 -0400] [Job 230] Closing foomatic-rip.
D [02/Jul/2006:11:13:05 -0400] PID 11361 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [02/Jul/2006:11:13:05 -0400] PID 11362 (/usr/lib/cups/backend/parallel) exited with no errors.
D [02/Jul/2006:11:13:05 -0400] [Job 230] File 0 is complete.
D [02/Jul/2006:11:13:05 -0400] Discarding unused job-completed event...
D [02/Jul/2006:11:13:05 -0400] Discarding unused printer-state-changed event...
D [02/Jul/2006:11:13:06 -0400] Unloading job 230...
D [02/Jul/2006:11:13:06 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:06 -0400] cupsdReadClient: 6 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:13:06 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:06 -0400] CUPS-Get-Printers
D [02/Jul/2006:11:13:06 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:06 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:06 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:06 -0400] cupsdReadClient: 6 POST /classes/ HTTP/1.1
D [02/Jul/2006:11:13:06 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:06 -0400] CUPS-Get-Classes
D [02/Jul/2006:11:13:06 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:06 -0400] cupsdAcceptClient: 9 from localhost:631 (IPv4)
D [02/Jul/2006:11:13:06 -0400] cupsdCloseClient: 6
D [02/Jul/2006:11:13:06 -0400] cupsdReadClient: 9 POST /printers/ HTTP/1.1
D [02/Jul/2006:11:13:06 -0400] cupsdAuthorize: No authentication data provided.
D [02/Jul/2006:11:13:06 -0400] CUPS-Get-Default
D [02/Jul/2006:11:13:06 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [02/Jul/2006:11:13:06 -0400] cupsdCloseClient: 9
D [02/Jul/2006:11:13:06 -0400] cupsdAcceptClient: 6 from localhost:631 (IPv4)

```
and then it goes on a little more with closing the cups and such.

Heres my pnm2ppa.conf file (the part about the model):
```

#-----------set the printer model---------------------------
# The printer model will normally  be set by a -v <model> command
# line argument.   Otherwise, if not set in the configuration file
# it defaults to the 710/720 series.   Remove/comment out the line
# "version 0" below to get the default choice.
# 
# If there is more than one "version" entry activated, the last one
# will be used.   The printer version can also be set with the command line
# option e.g., "-v 720".

version 712c
#version 720 #710, 712, 722 also acceptable
#version 820
#version 1000


#--------control system log messages from pnm2ppa-------------------
# pnm2ppa issues progress and error messages to the system log (syslog).
# For security reasons, no  input from the user is ever sent to the syslog.
# The setting "silent 1" suppresses messages to the syslog.   The
# setting "verbose 1"  sends messages to the standard error stream (stderr)
# in addition to the syslog. (Note: if pnm2ppa was compiled with the
# -D__NO_SYSLOG__ option (e.g., for BeOS),  syslog messages are
# diverted to stderr; use "silent 1" to suppress them.)

```

I have also modified the permissions on lp0 so that everyone can read and write.  I'm thinking that it has something to do with the  cupsdAuthorize: No authentication data provided. but everywhere I look says that the problem is solved but I cant see the solution....

Any help would be greatly apreciated :-)

---

### Post by BatteryCell on 2006-07-03
My bad, in the pnm2ppa.conf file I dont have 712c I just have 712.

---

### Post by BatteryCell on 2006-07-22
Come on Im sure that someone knows the answer... :D

---

### Post by BatteryCell on 2006-12-16
Well... I fixed it for dapper by restarting hplip and then restarting cups, but now in edgy it doesnt even detect the darned thing....if anyone has any ideas please tell.

---

### Post by BatteryCell on 2006-12-31
Update:
I did fix it by modprobing ppdev and then restarting cups (after already starting hplip).
```
modprobe ppdev
/etc/init.d/cupsys restart

```

---


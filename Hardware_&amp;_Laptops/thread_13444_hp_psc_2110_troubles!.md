---
title: "hp psc 2110 troubles!"
date: 2005-01-31
forum: Hardware &amp; Laptops
---

### Post by RJQuackQuack on 2005-01-31
I have this printer, but it doesn't print...  My cups error log reads 

I [31/Jan/2005:15:27:17 -0500] Setting PSC-2110 device-uri to "usb://Hewlett-Packard/PSC%202100%20Series?serial=MY2BID91020F" (was "file:/dev/null".)
I [31/Jan/2005:15:27:17 -0500] Setting PSC-2110 printer-is-accepting-jobs to 1 (was 0.)
I [31/Jan/2005:15:27:17 -0500] Setting PSC-2110 printer-state to 3 (was 5.)
I [31/Jan/2005:15:27:17 -0500] Saving printers.conf...
I [31/Jan/2005:15:27:17 -0500] New printer 'PSC-2110' added by 'root'.

when I try to add a printer.

The error log reads 

I [31/Jan/2005:15:27:43 -0500] Adding start banner page "none" to job 14.
I [31/Jan/2005:15:27:43 -0500] Adding end banner page "none" to job 14.
I [31/Jan/2005:15:27:43 -0500] Job 14 queued on 'PSC-2110' by 'alex'.
I [31/Jan/2005:15:27:43 -0500] Started filter /usr/lib/cups/filter/pstops (PID 30360) for job 14.
I [31/Jan/2005:15:27:43 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 30361) for job 14.
I [31/Jan/2005:15:27:43 -0500] Started backend /usr/lib/cups/backend/usb (PID 30362) for job 14.

when I print a test page.   The job stays permanently queued.


EDIT:  I tried using the hpoj package, but that has said "Probing "/dev/usb/lp0"...
"  for a long while.

EDIT 2:  I got HPOJ installed, but i still ahve the same problem when printing.
When I try to scan (XSane) I get the error "failed to start scanning, device is busy."

---

### Post by RJQuackQuack on 2005-01-31
Long Debug error log, I can see no problems:

Error Log on debug mode, I see no problems:

D [31/Jan/2005:16:08:16 -0500] CloseClient: 10
D [31/Jan/2005:16:08:16 -0500] ReadClient: 11 POST / HTTP/1.1
D [31/Jan/2005:16:08:16 -0500] ProcessIPPRequest: 11 status_code=1
D [31/Jan/2005:16:08:16 -0500] ReadClient: 4 POST / HTTP/1.1
D [31/Jan/2005:16:08:17 -0500] ProcessIPPRequest: 4 status_code=0
D [31/Jan/2005:16:08:17 -0500] CloseClient: 11
D [31/Jan/2005:16:08:17 -0500] ReadClient: 5 POST / HTTP/1.1
D [31/Jan/2005:16:08:17 -0500] ProcessIPPRequest: 5 status_code=0
D [31/Jan/2005:16:08:17 -0500] ReadClient: 9 POST / HTTP/1.1
D [31/Jan/2005:16:08:17 -0500] ProcessIPPRequest: 9 status_code=1
D [31/Jan/2005:16:08:19 -0500] ReadClient: 6 POST /printers/PSC-2110 HTTP/1.1
D [31/Jan/2005:16:08:19 -0500] print_job: auto-typing file...
D [31/Jan/2005:16:08:19 -0500] print_job: request file type is application/postscript.
D [31/Jan/2005:16:08:19 -0500] check_quotas: requesting-user-name = 'alex'
D [31/Jan/2005:16:08:19 -0500] print_job: requesting-user-name = 'alex'
D [31/Jan/2005:16:08:19 -0500] Adding default job-sheets values "none,none"...
I [31/Jan/2005:16:08:19 -0500] Adding start banner page "none" to job 1.
I [31/Jan/2005:16:08:19 -0500] Adding end banner page "none" to job 1.
I [31/Jan/2005:16:08:19 -0500] Job 1 queued on 'PSC-2110' by 'alex'.
D [31/Jan/2005:16:08:19 -0500] Job 1 hold_until = 0
D [31/Jan/2005:16:08:19 -0500] StartJob(1, 0x8185020)
D [31/Jan/2005:16:08:19 -0500] StartJob() id = 1, file = 0/1
D [31/Jan/2005:16:08:19 -0500] job-sheets=none,none
D [31/Jan/2005:16:08:19 -0500] banner_page = 0
D [31/Jan/2005:16:08:19 -0500] StartJob: argv = "PSC-2110","1","alex","Test Page","1","","/var/spool/cups/d00001-001"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[2]="USER=root"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[3]="CHARSET=iso-8859-1"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[4]="LANG=en_US"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[5]="TZ=US/Eastern"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[6]="PPD=/etc/cups/ppd/PSC-2110.ppd"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[11]="DEVICE_URI=ptal:/mlc:usb:PSC_2100_Series"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[12]="PRINTER=PSC-2110"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[15]="CUPS_SERVER=localhost"
D [31/Jan/2005:16:08:19 -0500] StartJob: envp[16]="IPP_PORT=631"
D [31/Jan/2005:16:08:19 -0500] StartJob: statusfds = [ 10 11 ]
D [31/Jan/2005:16:08:19 -0500] StartJob: filterfds[1] = [ 12 -1 ]
D [31/Jan/2005:16:08:19 -0500] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [31/Jan/2005:16:08:19 -0500] StartJob: filterfds[0] = [ 13 14 ]
D [31/Jan/2005:16:08:19 -0500] start_process("/usr/lib/cups/filter/pstops", 0xbfff0140, 0xbffef4b0, 12, 14, 11)
I [31/Jan/2005:16:08:19 -0500] Started filter /usr/lib/cups/filter/pstops (PID 4217) for job 1.
D [31/Jan/2005:16:08:19 -0500] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [31/Jan/2005:16:08:19 -0500] StartJob: filterfds[1] = [ 12 15 ]
D [31/Jan/2005:16:08:19 -0500] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbfff0140, 0xbffef4b0, 13, 15, 11)
I [31/Jan/2005:16:08:19 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4218) for job 1.
D [31/Jan/2005:16:08:19 -0500] StartJob: backend = "/usr/lib/cups/backend/ptal"
D [31/Jan/2005:16:08:19 -0500] StartJob: filterfds[0] = [ -1 13 ]
D [31/Jan/2005:16:08:19 -0500] start_process("/usr/lib/cups/backend/ptal", 0xbfff0140, 0xbffef4b0, 12, 13, 11)
I [31/Jan/2005:16:08:19 -0500] Started backend /usr/lib/cups/backend/ptal (PID 4219) for job 1.
D [31/Jan/2005:16:08:19 -0500] ProcessIPPRequest: 6 status_code=0
D [31/Jan/2005:16:08:19 -0500] [Job 1] Page = 595x842; 10,36 to 585,833
D [31/Jan/2005:16:08:19 -0500] [Job 1] slowcollate=0, slowduplex=0, sloworder=0
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%Title: PPR Test Page
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%Pages: 1
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%DocumentNeededResources: font Helvetica
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%EndComments
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%BeginProlog
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%EndProlog
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%BeginSetup
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%IncludeResource: font Helvetica
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%IncludeFeature: *PageSize Letter
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%EndSetup
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%Page: 1 1
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%Page: 1 1
D [31/Jan/2005:16:08:19 -0500] [Job 1] pw = 575.6, pl = 797.0
D [31/Jan/2005:16:08:19 -0500] [Job 1] PageLeft = 9.7, PageRight = 585.3
D [31/Jan/2005:16:08:19 -0500] [Job 1] PageTop = 833.0, PageBottom = 36.0
D [31/Jan/2005:16:08:19 -0500] [Job 1] PageWidth = 595.0, PageLength = 842.0
D [31/Jan/2005:16:08:19 -0500] [Job 1] 0 %%BeginDocument: /home/jdub/Documents/Canonical/Logos/Ubuntu_logo.eps
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%Title: Ubuntu final logo
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%Creator: FreeHand 10.0
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%CreationDate: 15/9/04 11:16 am
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%BoundingBox: 0 0 350 81
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%FHPathName:Work:CANONICAL SOFTWARE:Ubuntu:UBUNTU Identity:Ubuntu final logo
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%FHPageNum:1
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%DocumentSuppliedResources: procset Altsys_header 4 0
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%ColorUsage: Color
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%DocumentProcessColors: Black
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%DocumentCustomColors: (PANTONE 2965 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (PANTONE 151 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (PANTONE 1235 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (PANTONE 179 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (0r 43g 61b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (244r 72g 0b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (251r 139g 0b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ (212r 0g 0b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%CMYKCustomColor: 1 0.38 0 0.69 (PANTONE 2965 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0 0.43 0.87 0 (PANTONE 151 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0 0.275 0.76 0 (PANTONE 1235 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0 0.79 0.94 0 (PANTONE 179 CVC)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0.7613 0.5271 0.6244 0.7124 (0r 43g 61b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0.0017 0.7251 0.8508 0 (244r 72g 0b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0.0032 0.4248 0.8274 0 (251r 139g 0b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%+ 0.0176 0.9327 0.9184 0 (212r 0g 0b)
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%EndComments
D [31/Jan/2005:16:08:19 -0500] [Job 1] 1 %%BeginFont: Times-Roman
D [31/Jan/2005:16:08:19 -0500] [Job 1] ptal-connect: connecting to device "mlc:usb:PSC_2100_Series"...  successful.
D [31/Jan/2005:16:08:19 -0500] [Job 1] foomatic-rip version $Revision: 3.43.2.5 $ running...
D [31/Jan/2005:16:08:19 -0500] [Job 1] Parsing PPD file ...
D [31/Jan/2005:16:08:19 -0500] [Job 1] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option ColorSpace
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option Resolution
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option PageSize
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option PageRegion
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option Model
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option PrintoutMode
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option ImageableArea
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option PaperDimension
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option Duplex
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option Quality
D [31/Jan/2005:16:08:19 -0500] [Job 1] Added option Font
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] Parameter Summary
D [31/Jan/2005:16:08:19 -0500] [Job 1] -----------------
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] Spooler: cups
D [31/Jan/2005:16:08:19 -0500] [Job 1] Printer: PSC-2110
D [31/Jan/2005:16:08:19 -0500] [Job 1] PPD file: /etc/cups/ppd/PSC-2110.ppd
D [31/Jan/2005:16:08:19 -0500] [Job 1] Printer model: HP PSC 2110 Foomatic/hpijs (recommended)
D [31/Jan/2005:16:08:19 -0500] [Job 1] Job title: Test Page
D [31/Jan/2005:16:08:19 -0500] [Job 1] File(s) to be printed: 
D [31/Jan/2005:16:08:19 -0500] [Job 1] <STDIN>
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] ================================================
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] File: <STDIN>
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] ================================================
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] Reading PostScript input ...
D [31/Jan/2005:16:08:19 -0500] [Job 1] --> This document is DSC-conforming!
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] -----------
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%BeginProlog
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%EndProlog
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] -----------
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%BeginSetup
D [31/Jan/2005:16:08:19 -0500] [Job 1] Inserting PostScript code for CUPS' page accounting
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%BeginFeature: *PrintoutMode Normal
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: PrintoutMode=Normal --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: PrintoutMode=Normal --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%BeginFeature: *Quality FromPrintoutMode
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: Quality=FromPrintoutMode --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: Quality=FromPrintoutMode --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%BeginFeature: *PageSize A4
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: PageSize=A4 --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: PageSize=A4 --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%BeginFeature: *Duplex None
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: Duplex=None --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [31/Jan/2005:16:08:19 -0500] [Job 1] Option: Duplex=None --> Setting option
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found: %%EndSetup
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] -----------
D [31/Jan/2005:16:08:19 -0500] [Job 1] New page:  1 1
D [31/Jan/2005:16:08:19 -0500] [Job 1] Inserting option code into "PageSetup" section.
D [31/Jan/2005:16:08:19 -0500] [Job 1] No page header or page header not DSC-conforming
D [31/Jan/2005:16:08:19 -0500] [Job 1] Stopping search for page header options
D [31/Jan/2005:16:08:19 -0500] [Job 1] Found:
D [31/Jan/2005:16:08:19 -0500] [Job 1] 66BA0F2FBD4C92D25121A2647E8081BF05241DF408C9CE4EED2A630C3018869E51E7F90C030031A6E8FEE178DF9A598A4F1D8CA4C7741AA2C40081C0D48C29A8B4B60A0FE5D7BA4DD1F7CC51282CEF697AC70713546B0933B65246AAAC6A881DFB16
D [31/Jan/2005:16:08:19 -0500] [Job 1] --> Output goes directly to the renderer now.
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] Starting renderer
D [31/Jan/2005:16:08:19 -0500] [Job 1] JCL: <job data> 
D [31/Jan/2005:16:08:19 -0500] [Job 1] 
D [31/Jan/2005:16:08:19 -0500] [Job 1] renderer PID kid4=4224
D [31/Jan/2005:16:08:19 -0500] [Job 1] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5550" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2 -dIjsUseOutputFD -sOutputFile=- -
D [31/Jan/2005:16:08:19 -0500] [Job 1] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 5550' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2' '-dIjsUseOutputFD' '-sOutputFile=| cat >&3' '/dev/fd/0' 3>&1 1>&2
D [31/Jan/2005:16:08:20 -0500] AcceptClient: 11 from localhost:631.
D [31/Jan/2005:16:08:20 -0500] ReadClient: 11 POST / HTTP/1.1
D [31/Jan/2005:16:08:20 -0500] ProcessIPPRequest: 11 status_code=1
D [31/Jan/2005:16:08:20 -0500] AcceptClient: 12 from localhost:631.
D [31/Jan/2005:16:08:20 -0500] CloseClient: 11
D [31/Jan/2005:16:08:20 -0500] ReadClient: 12 POST / HTTP/1.1
D [31/Jan/2005:16:08:20 -0500] ProcessIPPRequest: 12 status_code=1
D [31/Jan/2005:16:08:20 -0500] ReadClient: 6 POST / HTTP/1.1
D [31/Jan/2005:16:08:20 -0500] ProcessIPPRequest: 6 status_code=0
D [31/Jan/2005:16:08:20 -0500] CloseClient: 12
D [31/Jan/2005:16:08:20 -0500] ReadClient: 7 POST / HTTP/1.1
D [31/Jan/2005:16:08:20 -0500] ProcessIPPRequest: 7 status_code=0
D [31/Jan/2005:16:08:20 -0500] ReadClient: 8 POST / HTTP/1.1
D [31/Jan/2005:16:08:20 -0500] ProcessIPPRequest: 8 status_code=1
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%EndFont
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%BeginResource: procset Altsys_header 4 0
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%EndResource
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%EndProlog
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%BeginSetup
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%IncludeResource: font Times-Roman
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%EndSetup
D [31/Jan/2005:16:08:20 -0500] [Job 1] Found: %%EndProlog
D [31/Jan/2005:16:08:20 -0500] [Job 1] 
D [31/Jan/2005:16:08:20 -0500] [Job 1] -----------
D [31/Jan/2005:16:08:20 -0500] [Job 1] Found: %%BeginSetup
D [31/Jan/2005:16:08:20 -0500] [Job 1] "%%BeginSetup" in page header
D [31/Jan/2005:16:08:20 -0500] [Job 1] Found: %%EndSetup
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%Trailer
D [31/Jan/2005:16:08:20 -0500] [Job 1] 1 %%EndDocument
D [31/Jan/2005:16:08:20 -0500] [Job 1] 0 %%Trailer
D [31/Jan/2005:16:08:20 -0500] [Job 1] Saw Trailer!
D [31/Jan/2005:16:08:20 -0500] [Job 1] Saw EOF!
D [31/Jan/2005:16:08:20 -0500] [Job 1] 
D [31/Jan/2005:16:08:20 -0500] [Job 1] Closing renderer
D [31/Jan/2005:16:08:21 -0500] AcceptClient: 11 from localhost:631.
D [31/Jan/2005:16:08:21 -0500] ReadClient: 11 POST / HTTP/1.1
D [31/Jan/2005:16:08:21 -0500] ProcessIPPRequest: 11 status_code=1
D [31/Jan/2005:16:08:21 -0500] AcceptClient: 12 from localhost:631.
D [31/Jan/2005:16:08:21 -0500] CloseClient: 11
D [31/Jan/2005:16:08:21 -0500] ReadClient: 12 POST / HTTP/1.1
D [31/Jan/2005:16:08:21 -0500] ProcessIPPRequest: 12 status_code=1
D [31/Jan/2005:16:08:21 -0500] CloseClient: 12
D [31/Jan/2005:16:08:21 -0500] ReadClient: 4 POST / HTTP/1.1
D [31/Jan/2005:16:08:22 -0500] ProcessIPPRequest: 4 status_code=0
D [31/Jan/2005:16:08:22 -0500] ReadClient: 5 POST / HTTP/1.1
D [31/Jan/2005:16:08:22 -0500] ProcessIPPRequest: 5 status_code=0
D [31/Jan/2005:16:08:22 -0500] ReadClient: 9 POST / HTTP/1.1
D [31/Jan/2005:16:08:22 -0500] ProcessIPPRequest: 9 status_code=1
D [31/Jan/2005:16:08:24 -0500] AcceptClient: 11 from localhost:631.
D [31/Jan/2005:16:08:24 -0500] ReadClient: 11 POST / HTTP/1.1
D [31/Jan/2005:16:08:24 -0500] ProcessIPPRequest: 11 status_code=1

---

### Post by paulgroovy on 2006-03-12
I have the same printer.  It scans, it coppies, but it will not print.  This is driving me crazy.  Does anybody have any ideas as to what it wrong here and how to fix it.  Thanks.

---

### Post by deladex on 2006-12-21
I managed to install the printer correctly.
Just follow the instruction on the link.

[http://hplip.sourceforge.net/install/index.html]("http://hplip.sourceforge.net/install/index.html")

The automatic installation got stuck, so i followed the instructions of the manual installation, and the printer is now working (printing and scanning)  :)

---


---
title: "Hoary 5.04 AMD64 Printer Problem"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by sylbal on 2005-04-12
Hi,

I'm trying to set up my HP Laserjet 6p on my fresh install of hoary and I'm getting into troubles.
I'm using Gnome configuration tool, first try with the 'Local Printer' way on parallel port 1, driver hpjs. Then another try with 'Network Printer' whith ipp://localhost/dev/lp0 URI.

The result is the same while trying to print test page, the job is correctly queued but not processed. I inspect /var/log/cups/error_log and I can't see any error around, just few lines with 'filter'. I restarted everytime cupsd when I was changing the config.

What am I doing wrong, ... ? Someone could help me ?
cheers,
-sb

---

### Post by kleeman on 2005-04-12
Here is a good troubleshooter. My advice is to increase the cups error logging to the debug level and recheck the logs and post back here:

[http://www.linuxprinting.org/error_log-faq.html](http://www.linuxprinting.org/error_log-faq.html)

---

### Post by sylbal on 2005-04-13
Hi,

I get back to the 'local Printer' mode setup by the gnome configuration tool, I moved to debug level and here's the dump, ... I'll look on the link you sent me.

I can see perl warnig, maybe it's the cause, ... ?


> 
D [13/Apr/2005:19:49:50 +0200] ReadClient: 4 POST / HTTP/1.1
D [13/Apr/2005:19:49:50 +0200] ProcessIPPRequest: 4 status_code=0
D [13/Apr/2005:19:49:51 +0200] ReadClient: 6 POST /printers/LaserJet-6P HTTP/1.1
D [13/Apr/2005:19:49:51 +0200] print_job: auto-typing file...
D [13/Apr/2005:19:49:51 +0200] print_job: request file type is application/postscript.
D [13/Apr/2005:19:49:51 +0200] check_quotas: requesting-user-name = 'sylvain'
D [13/Apr/2005:19:49:51 +0200] print_job: requesting-user-name = 'sylvain'
D [13/Apr/2005:19:49:51 +0200] Adding default job-sheets values "none,none"...
I [13/Apr/2005:19:49:51 +0200] Adding start banner page "none" to job 2.
I [13/Apr/2005:19:49:51 +0200] Adding end banner page "none" to job 2.
I [13/Apr/2005:19:49:51 +0200] Job 2 queued on 'LaserJet-6P' by 'sylvain'.
D [13/Apr/2005:19:49:51 +0200] Job 2 hold_until = 0
D [13/Apr/2005:19:49:51 +0200] StartJob(2, 0x6e9950)
D [13/Apr/2005:19:49:51 +0200] StartJob() id = 2, file = 0/1
D [13/Apr/2005:19:49:51 +0200] job-sheets=none,none
D [13/Apr/2005:19:49:51 +0200] banner_page = 0
D [13/Apr/2005:19:49:51 +0200] StartJob: argv = "LaserJet-6P","2","sylvain","Page de test","1","","/var/spool/cups/d00002-001"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[2]="USER=root"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[3]="CHARSET=utf-8"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[4]="LANG=fr"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[5]="TZ=Europe/Paris"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[6]="PPD=/etc/cups/ppd/LaserJet-6P.ppd"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[11]="DEVICE_URI=parallel:/dev/lp0"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[12]="PRINTER=LaserJet-6P"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[15]="CUPS_SERVER=localhost"
D [13/Apr/2005:19:49:51 +0200] StartJob: envp[16]="IPP_PORT=631"
D [13/Apr/2005:19:49:51 +0200] StartJob: statusfds = [ 7 8 ]
D [13/Apr/2005:19:49:51 +0200] StartJob: filterfds[1] = [ 10 -1 ]
D [13/Apr/2005:19:49:51 +0200] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [13/Apr/2005:19:49:51 +0200] StartJob: filterfds[0] = [ 11 12 ]
D [13/Apr/2005:19:49:51 +0200] start_process("/usr/lib/cups/filter/pstops", 0x7fbffefb20, 0x7fbffeed00, 10, 12, 8)
I [13/Apr/2005:19:49:51 +0200] Started filter /usr/lib/cups/filter/pstops (PID 7753) for job 2.
D [13/Apr/2005:19:49:51 +0200] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [13/Apr/2005:19:49:51 +0200] StartJob: filterfds[1] = [ 10 13 ]
D [13/Apr/2005:19:49:51 +0200] start_process("/usr/lib/cups/filter/foomatic-rip", 0x7fbffefb20, 0x7fbffeed00, 11, 13, 8)
I [13/Apr/2005:19:49:51 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7754) for job 2.
D [13/Apr/2005:19:49:51 +0200] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [13/Apr/2005:19:49:51 +0200] StartJob: filterfds[0] = [ -1 11 ]
D [13/Apr/2005:19:49:51 +0200] start_process("/usr/lib/cups/backend/parallel", 0x7fbffefb20, 0x7fbffeed00, 10, 11, 8)
I [13/Apr/2005:19:49:51 +0200] Started backend /usr/lib/cups/backend/parallel (PID 7755) for job 2.
D [13/Apr/2005:19:49:51 +0200] ProcessIPPRequest: 6 status_code=0
D [13/Apr/2005:19:49:51 +0200] [Job 2] Page = 595x842; 18,14 to 577,828
D [13/Apr/2005:19:49:51 +0200] [Job 2] slowcollate=0, slowduplex=0, sloworder=0
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%Title: PPR Test Page
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%Pages: 1
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%DocumentNeededResources: font Helvetica
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%EndComments
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%BeginProlog
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%EndProlog
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%BeginSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%IncludeResource: font Helvetica
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%IncludeFeature: *PageSize A4
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%EndSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%Page: 1 1
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%Page: 1 1
D [13/Apr/2005:19:49:51 +0200] [Job 2] pw = 559.0, pl = 813.2
D [13/Apr/2005:19:49:51 +0200] [Job 2] PageLeft = 18.0, PageRight = 577.0
D [13/Apr/2005:19:49:51 +0200] [Job 2] PageTop = 827.6, PageBottom = 14.4
D [13/Apr/2005:19:49:51 +0200] [Job 2] PageWidth = 595.0, PageLength = 842.0
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%BeginDocument: /home/jdub/Documents/Canonical/Logos/Ubuntu_logo.eps
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%Title: Ubuntu final logo
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%Creator: FreeHand 10.0
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%CreationDate: 15/9/04 11:16 am
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%BoundingBox: 0 0 350 81
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%FHPathName:Work:CANONICAL SOFTWARE:Ubuntu:UBUNTU Identity:Ubuntu final logo
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%FHPageNum:1
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%DocumentSuppliedResources: procset Altsys_header 4 0
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%ColorUsage: Color
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%DocumentProcessColors: Black
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%DocumentCustomColors: (PANTONE 2965 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (PANTONE 151 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (PANTONE 1235 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (PANTONE 179 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (0r 43g 61b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (244r 72g 0b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (251r 139g 0b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ (212r 0g 0b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%CMYKCustomColor: 1 0.38 0 0.69 (PANTONE 2965 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0 0.43 0.87 0 (PANTONE 151 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0 0.275 0.76 0 (PANTONE 1235 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0 0.79 0.94 0 (PANTONE 179 CVC)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0.7613 0.5271 0.6244 0.7124 (0r 43g 61b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0.0017 0.7251 0.8508 0 (244r 72g 0b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0.0032 0.4248 0.8274 0 (251r 139g 0b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%+ 0.0176 0.9327 0.9184 0 (212r 0g 0b)
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%EndComments
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%BeginFont: Times-Roman
D [13/Apr/2005:19:49:51 +0200] [Job 2] perl: warning: Setting locale failed.
D [13/Apr/2005:19:49:51 +0200] [Job 2] perl: warning: Please check that your locale settings:
D [13/Apr/2005:19:49:51 +0200] [Job 2] LANGUAGE = (unset),
D [13/Apr/2005:19:49:51 +0200] [Job 2] LC_ALL = (unset),
D [13/Apr/2005:19:49:51 +0200] [Job 2] LANG = "fr"
D [13/Apr/2005:19:49:51 +0200] [Job 2] are supported and installed on your system.
D [13/Apr/2005:19:49:51 +0200] [Job 2] perl: warning: Falling back to the standard locale ("C").
D [13/Apr/2005:19:49:51 +0200] [Job 2] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [13/Apr/2005:19:49:51 +0200] [Job 2] Parsing PPD file ...
D [13/Apr/2005:19:49:51 +0200] [Job 2] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option ColorSpace
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Resolution
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option PageSize
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option PageRegion
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Model
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option PrintoutMode
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option ImageableArea
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option PaperDimension
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option InputSlot
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Manualfeed
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Duplex
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Economode
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Copies
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option REt
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option TonerDensity
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option MPTray
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Quality
D [13/Apr/2005:19:49:51 +0200] [Job 2] Added option Font
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] Parameter Summary
D [13/Apr/2005:19:49:51 +0200] [Job 2] -----------------
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] Spooler: cups
D [13/Apr/2005:19:49:51 +0200] [Job 2] Printer: LaserJet-6P
D [13/Apr/2005:19:49:51 +0200] [Job 2] PPD file: /etc/cups/ppd/LaserJet-6P.ppd
D [13/Apr/2005:19:49:51 +0200] [Job 2] Printer model: HP LaserJet 6P Foomatic/hpijs (recommended)
D [13/Apr/2005:19:49:51 +0200] [Job 2] Job title: Page de test
D [13/Apr/2005:19:49:51 +0200] [Job 2] File(s) to be printed: 
D [13/Apr/2005:19:49:51 +0200] [Job 2] <STDIN>
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] ================================================
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] File: <STDIN>
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] ================================================
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] Reading PostScript input ...
D [13/Apr/2005:19:49:51 +0200] [Job 2] --> This document is DSC-conforming!
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] -----------
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginProlog
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%EndProlog
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] -----------
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] Inserting PostScript code for CUPS' page accounting
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *PrintoutMode Normal
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: PrintoutMode=Normal --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: PrintoutMode=Normal --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *REt Medium
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: REt=Medium --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: REt=Medium
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: REt=Medium --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *TonerDensity 5
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: TonerDensity=5 --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: TonerDensity=5
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: TonerDensity=5 --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *InputSlot Default
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: InputSlot=Default --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: InputSlot=Default --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *Copies 1
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Copies=1 --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: Copies=1
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Copies=1 --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *Economode Off
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Economode=Off --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: Economode=Off
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Economode=Off --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *MPTray First
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: MPTray=First --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: MPTray=First
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: MPTray=First --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *Quality FromPrintoutMode
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Quality=FromPrintoutMode --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Quality=FromPrintoutMode --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *PageRegion A4
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: PageRegion=A4 --> Option will be set by PostScript interpreter
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: PageSize=A4 --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginFeature: *Duplex None
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Duplex=None --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [13/Apr/2005:19:49:51 +0200] [Job 2] Option: Duplex=None --> Setting option
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%EndSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] -----------
D [13/Apr/2005:19:49:51 +0200] [Job 2] New page:  1 1
D [13/Apr/2005:19:49:51 +0200] [Job 2] Inserting option code into "PageSetup" section.
D [13/Apr/2005:19:49:51 +0200] [Job 2] No page header or page header not DSC-conforming
D [13/Apr/2005:19:49:51 +0200] [Job 2] Stopping search for page header options
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found:
D [13/Apr/2005:19:49:51 +0200] [Job 2] 66BA0F2FBD4C92D25121A2647E8081BF05241DF408C9CE4EED2A630C3018869E51E7F90C030031A6E8FEE178DF9A598A4F1D8CA4C7741AA2C40081C0D48C29A8B4B60A0FE5D7BA4DD1F7CC51282CEF697AC70713546B0933B65246AAAC6A881DFB16
D [13/Apr/2005:19:49:51 +0200] [Job 2] --> Output goes directly to the renderer now.
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] Starting renderer
D [13/Apr/2005:19:49:51 +0200] [Job 2] JCL: %-12345X@PJL
D [13/Apr/2005:19:49:51 +0200] [Job 2] @PJL SET MANUALFEED=OFF
D [13/Apr/2005:19:49:51 +0200] [Job 2] @PJL SET ECONOMODE=OFF
D [13/Apr/2005:19:49:51 +0200] [Job 2] @PJL SET COPIES=1
D [13/Apr/2005:19:49:51 +0200] [Job 2] @PJL SET RET=MEDIUM
D [13/Apr/2005:19:49:51 +0200] [Job 2] @PJL SET DENSITY=5
D [13/Apr/2005:19:49:51 +0200] [Job 2] @PJL SET MPTRAY=FIRST
D [13/Apr/2005:19:49:51 +0200] [Job 2] <job data> 
D [13/Apr/2005:19:49:51 +0200] [Job 2] %-12345X@PJL RESET
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] renderer PID kid4=7757
D [13/Apr/2005:19:49:51 +0200] [Job 2] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=- -
D [13/Apr/2005:19:49:51 +0200] [Job 2] perl: warning: Setting locale failed.
D [13/Apr/2005:19:49:51 +0200] [Job 2] perl: warning: Please check that your locale settings:
D [13/Apr/2005:19:49:51 +0200] [Job 2] LANGUAGE = (unset),
D [13/Apr/2005:19:49:51 +0200] [Job 2] LC_ALL = (unset),
D [13/Apr/2005:19:49:51 +0200] [Job 2] LANG = "fr"
D [13/Apr/2005:19:49:51 +0200] [Job 2] are supported and installed on your system.
D [13/Apr/2005:19:49:51 +0200] [Job 2] perl: warning: Falling back to the standard locale ("C").
D [13/Apr/2005:19:49:51 +0200] [Job 2] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=HP LaserJet' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%EndFont
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%BeginResource: procset Altsys_header 4 0
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%EndResource
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%EndProlog
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%BeginSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%IncludeResource: font Times-Roman
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%EndSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%EndProlog
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] -----------
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%BeginSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] "%%BeginSetup" in page header
D [13/Apr/2005:19:49:51 +0200] [Job 2] Found: %%EndSetup
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%Trailer
D [13/Apr/2005:19:49:51 +0200] [Job 2] 1 %%EndDocument
D [13/Apr/2005:19:49:51 +0200] [Job 2] 0 %%Trailer
D [13/Apr/2005:19:49:51 +0200] [Job 2] Saw Trailer!
D [13/Apr/2005:19:49:51 +0200] [Job 2] Saw EOF!
D [13/Apr/2005:19:49:51 +0200] [Job 2] 
D [13/Apr/2005:19:49:51 +0200] [Job 2] Closing renderer
D [13/Apr/2005:19:49:52 +0200] ReadClient: 4 POST / HTTP/1.1
D [13/Apr/2005:19:49:52 +0200] ProcessIPPRequest: 4 status_code=0


---

### Post by sylbal on 2005-04-13
I added 'gs' package adn now the printer is 'moving' I have at least a little sign of life. I have lots of pages with single top line of characters, ... I continue my quest, ...

---

### Post by BuggerOne on 2005-05-20
Hello,

I had the same problem with kubuntu Hoary.
My LaserJet 6P was not printing. The leds just blink saying error and some dummy characters are printed on top of the page.
The printer was working fine with windows.

I finaly change the cable and now everything is ok !! It sound strange to me that a cable work with windows but not with linux, but it is !

hope that helps !

---

### Post by David Haas on 2005-05-22
I gather that your printer is recognized as shown by being listed correctly under the printer icon in gnome-printer-manager. Then, what ppd file did you choose ("open")? I see that 2 are listed in foomatic-ppds/HP: HP-LaserJet_6P-hpijs.ppd.gz and HP-LaserJet_6P-ljet4.ppd.gz.I don't know the difference, if any, between them, but I believe that the hpijs ones are written by HP and donated to the Linux community for free.  Once your ppd file is selected, it should appear in /etc/cups/ppd. So, you could check on this.  
David

---


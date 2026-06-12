---
title: "[Gutsy+CUPS] HP Printer..just empty pages after upgrading"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by sherz on 2007-11-13
Hi I am having a problem with my HP Printer after upgrading to gutsy.

I am running a server with gutsy (SPARC) and  I am even from the XP -Client able to print to the HP Network printer but the pages are just empty.

I used [PrintingBugInfoScript]("https://wiki.ubuntu.com/PrintingBugInfoScript") to give more information about my system:





```

ProblemType: printingbuginfo v2.0: printingbug+locallpt (https://wiki.ubuntu.com/PrintingBugInfoScript)
CupsConfiguredDevices: 
CupsConfiguredPPDs: HP: HP LaserJet 4050 Foomatic/hpijs
Date: Tue Nov 13 22:23:00 2007
DesktopEnvironment: none
DistroRelease: Ubuntu 7.10
EtcPapersize: letter
InstalledPrintingPackages:
 ii  cupsys                   1.3.2-1ubuntu7.1         Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.1-0ubuntu8           printer drivers for CUPS
 ii  foo2zjs                  20070625-0ubuntu1        Support for printing to ZjStream-based printers
 ii  foomatic-db              20070919-0ubuntu3        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070719-0ubuntu4  OpenPrinting printer support - programs
 ii  foomatic-db-hpijs        20070813-0ubuntu1        OpenPrinting printer support - database for HPIJS driver
 ii  foomatic-filters         3.0.2-20070719-0ubuntu1  OpenPrinting printer support - filters
 ii  ghostscript              8.61.dfsg.1~svn8187-0ubu The GPL Ghostscript PostScript/PDF interpreter
 ii  gnome-cups-manager       0.31-3ubuntu5            CUPS printer admin tool for GNOME
 ii  gs-common                8.61.dfsg.1~svn8187-0ubu Transitional package
 ii  gs-esp                   8.61.dfsg.1~svn8187-0ubu Transitional package
 ii  hpijs                    2.7.7+2.7.7.dfsg.1-0ubun HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.7.7.dfsg.1-0ubuntu5    HP Linux Printing and Imaging System (HPLIP)
 ii  hpoj                     0.91-12build1            HP OfficeJet Linux driver (hpoj)
 ii  libgnomeprint2.2-0       2.18.2-0ubuntu1          The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
Locale: LANG=en_US.UTF-8, LC_CTYPE=en_US.UTF-8, LC_PAPER=en_US.UTF-8
LptPrinterDevices:
 crw-rw---- 1 root lp 6, 0 Nov 13 18:43 /dev/lp0
 crw-rw---- 1 root lp 99, 0 Nov 13 18:43 /dev/parport0
LptPrinterIEEE1284Id:
 /dev/parport0:
 
LptPrinterKernelModules:
 ppdev                  11528  0 
 lp                     14040  0 
 parport                43600  3 ppdev,parport_pc,lp
Uname: Linux sun.XXXX  2.6.22-14-sparc64 #1 Sun Oct 14 21:57:46 GMT 2007 sparc64 GNU/Linux

```


What could it be ??

---

### Post by 11hjpphty76lkjj on 2007-11-13
Edit  /etc/cups/cupsd.conf

Change "loglevel" to 'debug'

Run ```
tail -f /var/log/cups/error_log
```

Try and print, post the cups error log.

Your systems looks fine....but there may be something corrupt, I'm thinking in ghostscript.  But lets look at the log and see what's going on.  You can get more info on the cups log here:

[http://hplip.sourceforge.net/troubleshooting/printing.html](http://hplip.sourceforge.net/troubleshooting/printing.html)

and look at issue 2.

---

### Post by sherz on 2007-11-14
Ok here you go:
```

D [14/Nov/2007:10:03:45 +0000] print_job: auto-typing file...
D [14/Nov/2007:10:03:45 +0000] add_job: requesting-user-name="Bill"
D [14/Nov/2007:10:03:45 +0000] Adding default job-sheets values "none,none"...
I [14/Nov/2007:10:03:45 +0000] [Job 37] Adding start banner page "none".
D [14/Nov/2007:10:03:45 +0000] Discarding unused job-created event...
I [14/Nov/2007:10:03:45 +0000] [Job 37] Adding job file of type application/postscript.
I [14/Nov/2007:10:03:45 +0000] [Job 37] Adding end banner page "none".
I [14/Nov/2007:10:03:45 +0000] [Job 37] Queued on "HP" by "Bill".
D [14/Nov/2007:10:03:45 +0000] [Job 37] hold_until = 0
D [14/Nov/2007:10:03:45 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:45 +0000] [Job 37] job-sheets=none,none
D [14/Nov/2007:10:03:45 +0000] [Job 37] banner_page = 0
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[0]="HP"
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[1]="37"
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[2]="Bill"
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[3]="Welcome page"
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[4]="1"
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[5]="job-uuid=urn:uuid:12cc6da0-fef0-34b8-6963-358c7c398908"
D [14/Nov/2007:10:03:45 +0000] [Job 37] argv[6]="/var/spool/cups/d00037-001"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[9]="SERVER_ADMIN=root@sun.XXX"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[10]="SOFTWARE=CUPS/1.3.2"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[12]="TZ=User defined"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[13]="USER=root"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[16]="IPP_PORT=631"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[17]="CHARSET=utf-8"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[18]="LANG=en_US"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[19]="PPD=/etc/cups/ppd/HP.ppd"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[20]="RIP_MAX_CACHE=8m"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[21]="CONTENT_TYPE=application/postscript"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[22]="DEVICE_URI=socket://10.100.0.200"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[23]="PRINTER=HP"
D [14/Nov/2007:10:03:45 +0000] [Job 37] envp[24]="FINAL_CONTENT_TYPE=printer/HP"
I [14/Nov/2007:10:03:45 +0000] [Job 37] Started filter /usr/lib/cups/filter/pstops (PID 19406)
I [14/Nov/2007:10:03:45 +0000] [Job 37] Started filter /usr/lib/cups/filter/foomatic-rip (PID 19407)
I [14/Nov/2007:10:03:45 +0000] [Job 37] Started backend /usr/lib/cups/backend/socket (PID 19408)
D [14/Nov/2007:10:03:45 +0000] Discarding unused job-state event...
D [14/Nov/2007:10:03:45 +0000] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [14/Nov/2007:10:03:45 +0000] [Job 37] perl: warning: Setting locale failed.
D [14/Nov/2007:10:03:45 +0000] [Job 37] perl: warning: Please check that your locale settings:
D [14/Nov/2007:10:03:45 +0000] [Job 37] LANGUAGE = (unset),
D [14/Nov/2007:10:03:45 +0000] [Job 37] LC_ALL = (unset),
D [14/Nov/2007:10:03:45 +0000] [Job 37] LANG = "en_US"
D [14/Nov/2007:10:03:45 +0000] [Job 37] are supported and installed on your system.
D [14/Nov/2007:10:03:45 +0000] [Job 37] perl: warning: Falling back to the standard locale ("C").
D [14/Nov/2007:10:03:45 +0000] [Job 37] Page = 612x792; 18,14 to 594,778
D [14/Nov/2007:10:03:45 +0000] [Job 37] slow_collate=0, slow_duplex=0, slow_order=0
D [14/Nov/2007:10:03:45 +0000] [Job 37] Skipping PJL header...
D [14/Nov/2007:10:03:45 +0000] [Job 37] Before copy_comments - %!PS-Adobe-3.0
D [14/Nov/2007:10:03:45 +0000] [Job 37] %!PS-Adobe-3.0
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%Title: Welcome page
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%Creator: PScript5.dll Version 5.2.2
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%CreationDate: 11/14/2007 11:3:35
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%For: Bill
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%BoundingBox: (atend)
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%DocumentNeededResources: (atend)
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%DocumentSuppliedResources: (atend)
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%DocumentData: Clean7Bit
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%TargetDevice: (HP LaserJet 4050 Series ) (2014.108) 1
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%LanguageLevel: 2
D [14/Nov/2007:10:03:45 +0000] [Job 37] %%EndComments
E [14/Nov/2007:10:03:45 +0000] [Job 37] No %%Pages: comment in header!
D [14/Nov/2007:10:03:45 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:45 +0000] [Job 37] Before copy_prolog - 
D [14/Nov/2007:10:03:45 +0000] [Job 37] Before copy_setup - 
D [14/Nov/2007:10:03:45 +0000] [Job 37] Before page loop - %%Trailer
D [14/Nov/2007:10:03:45 +0000] [Job 37] Wrote 0 pages...
D [14/Nov/2007:10:03:45 +0000] PID 19406 (/usr/lib/cups/filter/pstops) exited with no errors.
D [14/Nov/2007:10:03:45 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:46 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:46 +0000] [Job 37] Connected to 10.100.0.200:9100 (IPv4)...
D [14/Nov/2007:10:03:46 +0000] [Job 37] backendRunLoop(print_fd=0, device_fd=8, use_bc=1, side_cb=0x10fc8)
D [14/Nov/2007:10:03:46 +0000] [Job 37] foomatic-rip version $Revision$ running...
D [14/Nov/2007:10:03:46 +0000] [Job 37] Parsing PPD file ...
D [14/Nov/2007:10:03:46 +0000] [Job 37] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option ColorSpace
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option Resolution
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option PageSize
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option PageRegion
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option Model
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option PrintoutMode
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option InputSlot
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option ImageableArea
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option PaperDimension
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option Duplex
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option Quality
D [14/Nov/2007:10:03:46 +0000] [Job 37] Added option Font
D [14/Nov/2007:10:03:46 +0000] cupsdReadClient: 14 POST /printers/HP HTTP/1.1
D [14/Nov/2007:10:03:46 +0000] cupsdAuthorize: No authentication data provided.
D [14/Nov/2007:10:03:46 +0000] Get-Printer-Attributes https://sun.XXX:631/printers/HP
D [14/Nov/2007:10:03:46 +0000] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Parameter Summary
D [14/Nov/2007:10:03:46 +0000] [Job 37] -----------------
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Spooler: cups
D [14/Nov/2007:10:03:46 +0000] [Job 37] Printer: HP
D [14/Nov/2007:10:03:46 +0000] [Job 37] Shell: /bin/bash
D [14/Nov/2007:10:03:46 +0000] [Job 37] PPD file: /etc/cups/ppd/HP.ppd
D [14/Nov/2007:10:03:46 +0000] [Job 37] ATTR file: 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Printer model: HP LaserJet 4050 Foomatic/hpijs
D [14/Nov/2007:10:03:46 +0000] [Job 37] Job title: Welcome page
D [14/Nov/2007:10:03:46 +0000] [Job 37] File(s) to be printed: 
D [14/Nov/2007:10:03:46 +0000] [Job 37] <STDIN>
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [14/Nov/2007:10:03:46 +0000] [Job 37] Pondering option 'job-uuid=urn:uuid:12cc6da0-fef0-34b8-6963-358c7c398908'
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option job-uuid=urn:uuid:12cc6da0-fef0-34b8-6963-358c7c398908.
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] ================================================
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] File: <STDIN>
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] ================================================
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Reading PostScript input ...
D [14/Nov/2007:10:03:46 +0000] [Job 37] --> This document is DSC-conforming!
D [14/Nov/2007:10:03:46 +0000] [Job 37] Job claims to be DSC-conforming, but "%%BeginProlog" was missing before first line with another "%%Begin..." comment (is this a TeX/LaTeX/dvips-generated PostScript file?). Assuming start of "Prolog" here.
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] -----------
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginProlog
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%EndProlog
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] -----------
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginSetup
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *PrintoutMode Normal
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: PrintoutMode=Normal --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: PrintoutMode=Normal --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *InputSlot Default
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: InputSlot=Default --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: InputSlot=Default --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Quality FromPrintoutMode
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: Quality=FromPrintoutMode --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: Quality=FromPrintoutMode --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *PageRegion Letter
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: PageRegion=Letter --> Option will be set by PostScript interpreter
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %% FoomaticRIPOptionSetting: PageSize=Letter
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: PageSize=Letter --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Duplex None
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: Duplex=None --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: Duplex=None --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *HPPaperPolicy PromptUser
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option HPPaperPolicy=PromptUser found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *HPHalftone PrinterDefault
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option HPHalftone=PrinterDefault found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Collate False
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option Collate=False found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Smoothing True
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option Smoothing=True found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *PageSize Letter
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: PageSize=Letter --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *MediaType None
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option MediaType=None found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Duplex None
D [14/Nov/2007:10:03:46 +0000] [Job 37] Option: Duplex=None --> Setting option
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *HPPrinterModelName HP_LaserJet_4050_Series_PS
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option HPPrinterModelName=HP_LaserJet_4050_Series_PS found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *JRConstraints JRCHDFull
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option JRConstraints=JRCHDFull found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *OptionTrays 2Trays
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option OptionTrays=2Trays found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Option3 False
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option Option3=False found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *Option5 False
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option Option5=False found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *InstalledMemory 8MB
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option InstalledMemory=8MB found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *PrinterHardDisk False
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option PrinterHardDisk=False found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginFeature: *JobRetention False
D [14/Nov/2007:10:03:46 +0000] [Job 37] Unknown option JobRetention=False found in the job
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%EndSetup
D [14/Nov/2007:10:03:46 +0000] [Job 37] Inserting PostScript code for CUPS' page accounting
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%BeginPageSetup
D [14/Nov/2007:10:03:46 +0000] [Job 37] Found: %%EndPageSetup
D [14/Nov/2007:10:03:46 +0000] [Job 37] End of page header
D [14/Nov/2007:10:03:46 +0000] [Job 37] Flushing FIFO.
D [14/Nov/2007:10:03:46 +0000] [Job 37] "PageSetup" section is missing, inserting it.
D [14/Nov/2007:10:03:46 +0000] [Job 37] Inserting option code into "PageSetup" section.
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Starting renderer
D [14/Nov/2007:10:03:46 +0000] [Job 37] JCL: <job data> 
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] renderer PID kid4=19416
D [14/Nov/2007:10:03:46 +0000] [Job 37] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=- -
D [14/Nov/2007:10:03:46 +0000] [Job 37] 
D [14/Nov/2007:10:03:46 +0000] [Job 37] Closing renderer
D [14/Nov/2007:10:03:46 +0000] [Job 37] perl: warning: Setting locale failed.
D [14/Nov/2007:10:03:46 +0000] [Job 37] perl: warning: Please check that your locale settings:
D [14/Nov/2007:10:03:46 +0000] [Job 37] LANGUAGE = (unset),
D [14/Nov/2007:10:03:46 +0000] [Job 37] LC_ALL = (unset),
D [14/Nov/2007:10:03:46 +0000] [Job 37] LANG = "en_US"
D [14/Nov/2007:10:03:46 +0000] [Job 37] are supported and installed on your system.
D [14/Nov/2007:10:03:46 +0000] [Job 37] perl: warning: Falling back to the standard locale ("C").
D [14/Nov/2007:10:03:49 +0000] [Job 37] foomatic-gswrapper: gs '-sstdout=%stderr' '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=HP LaserJet' '-dDEVICEWIDTHPOINTS=612' '-dDEVICEHEIGHTPOINTS=792' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=%stdout' '-'
D [14/Nov/2007:10:03:50 +0000] [Job 37] %%[ ProductName: GPL Ghostscript SVN PRE-RELEASE ]%%
D [14/Nov/2007:10:03:51 +0000] Discarding unused job-progress event...
D [14/Nov/2007:10:03:53 +0000] [Job 37] %%[Page: 1]%%
D [14/Nov/2007:10:03:53 +0000] [Job 37] %%[LastPage]%%
D [14/Nov/2007:10:03:53 +0000] [Job 37] tail process done writing data to STDOUT
D [14/Nov/2007:10:03:53 +0000] [Job 37] KID4 finished
D [14/Nov/2007:10:03:53 +0000] [Job 37] KID3 exited with status 0
D [14/Nov/2007:10:03:53 +0000] [Job 37] KID4 exited with status 0
D [14/Nov/2007:10:03:53 +0000] [Job 37] Renderer exit stat: 0
D [14/Nov/2007:10:03:53 +0000] [Job 37] Read 934 bytes of print data...
D [14/Nov/2007:10:03:53 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:53 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:53 +0000] [Job 37] Wrote 934 bytes of print data...
D [14/Nov/2007:10:03:53 +0000] [Job 37] KID3 finished
D [14/Nov/2007:10:03:53 +0000] [Job 37] Renderer process finished
D [14/Nov/2007:10:03:53 +0000] [Job 37] 
D [14/Nov/2007:10:03:53 +0000] [Job 37] Closing foomatic-rip.
D [14/Nov/2007:10:03:53 +0000] PID 19407 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [14/Nov/2007:10:03:58 +0000] PID 19408 (/usr/lib/cups/backend/socket) exited with no errors.
D [14/Nov/2007:10:03:58 +0000] [Job 37] File 0 is complete.
I [14/Nov/2007:10:03:58 +0000] [Job 37] Completed successfully.
D [14/Nov/2007:10:03:58 +0000] Discarding unused printer-state-changed event...
D [14/Nov/2007:10:03:58 +0000] Discarding unused job-completed event...
D [14/Nov/2007:10:03:59 +0000] [Job 37] Unloading...

```

---

### Post by 11hjpphty76lkjj on 2007-11-14
Everything looks okay.  Run:

```
ps ax | grep hpoj 
```

and post the output.

A

---

### Post by sherz on 2007-11-14
its quite strange because its seems to run but when I check with ps then it doesn't

```
 /etc/init.d/hpoj start

Stopping the HP OfficeJet Linux driver.
Starting the HP OfficeJet Linux driver.
    hpjd:10.100.0.200

root@sun:/etc/init.d# ps ax | grep hpoj
 5024 pts/0    R+     0:00 grep hpoj

```

---

### Post by 11hjpphty76lkjj on 2007-11-14
Sorry for not a better explanation.   We do not want HPOJ running.  In fact you can remove it,

```
sudo apt-get remove hpoj
```

I wanted to see if it was running by default and that could be the cause of the problem because hpoj and hplip don't work together.  In fact I'm honestly confused why hpoj is coming with ubuntu as it's really really old and not supported anymore.

A

---

### Post by sherz on 2007-11-14
Ok I did this. 

But it's still the same

---

### Post by 11hjpphty76lkjj on 2007-11-14
possible for you to try removing hplip and installing from source from [http://hplip.sf.net](http://hplip.sf.net) ? 

A

---


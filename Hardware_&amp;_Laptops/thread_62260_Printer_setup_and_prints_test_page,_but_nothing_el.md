---
title: "Printer setup and prints test page, but nothing else"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by filemanager on 2005-09-04
I have an Epson stylus CX5400. It worked perfectly. Then my computer died and I had to reinstall everything. So when I reinstalled my printer everything was good, the test page printed fine.

But now, when I go into the Word processor, it doesn't recognize the printer. It just says 'Generic Printer' and if you try to print it doesn't do anything.

Help!

---

### Post by nbcthreat on 2005-10-07
I have a similar problem. Test pages print fine, but I can't print from firefox.

Openoffice seems to print, but only in A5 page format, which is wrong.

Any sort of attempt to access the printer with "lp" type commands returns 

lp: Unable to access "PIXUS-iP4100-Ver.2.50" - No such file or directory

---

### Post by David Haas on 2005-10-08
filemanager--I assume that when you re-installed Ubuntu Hoary the cups and foomatic packages were installed by default (?) You could check this in Synaptic. I see that Ubuntu contains in the default packages the driver (PPD file) for the Epson Stylus CX5400. It's escp2-cx5400.ppd.gz and it's in the gimp-print/4.2 directory at /usr/share/cups/model/gimp-print/4.2. After selecting it in the Gnome Printing Manager Linux should place an unzipped copy in /etc/cups/ppd. Do you have such a copy there? I hope that checking these things might get you closer to a solution.
David

---

### Post by elfgoh on 2005-10-12
Hi, u may find this link useful:

[http://episteme.arstechnica.com/groupee/forums/a/tpc/f/96509133/m/46500535695/r/46500535695](http://episteme.arstechnica.com/groupee/forums/a/tpc/f/96509133/m/46500535695/r/46500535695)

I have the same problem as you did.

In a nutshell, I did a complete removal of lprng in synaptic. It allowed OOo, opera, and mozilla to print. However, the print size was B2 size instead of A4!! Still trying to solve that at the moment....

Maybe u guys wanna take a look at my log file? I'm not sure exactly where it starts, so this is gg to be a bit chunky =) Hope the tip helps.

D [12/Oct/2005:00:03:53 +0800] ProcessIPPRequest: 8 status_code=1
D [12/Oct/2005:00:03:53 +0800] ReadClient: 8 POST / HTTP/1.1
D [12/Oct/2005:00:03:54 +0800] ProcessIPPRequest: 8 status_code=1
D [12/Oct/2005:00:03:54 +0800] ReadClient: 8 POST / HTTP/1.1
D [12/Oct/2005:00:03:54 +0800] ProcessIPPRequest: 8 status_code=0
D [12/Oct/2005:00:03:54 +0800] CloseClient: 8
D [12/Oct/2005:00:03:54 +0800] AcceptClient: 8 from localhost:631.
D [12/Oct/2005:00:03:54 +0800] ReadClient: 8 POST /printers/BJC-600 HTTP/1.1
D [12/Oct/2005:00:03:54 +0800] print_job: auto-typing file...
D [12/Oct/2005:00:03:54 +0800] print_job: request file type is application/postscript.
D [12/Oct/2005:00:03:54 +0800] check_quotas: requesting-user-name = 'goh'
D [12/Oct/2005:00:03:54 +0800] print_job: requesting-user-name = 'goh'
I [12/Oct/2005:00:03:54 +0800] Adding start banner page "none" to job 91.
I [12/Oct/2005:00:03:54 +0800] Adding end banner page "none" to job 91.
I [12/Oct/2005:00:03:54 +0800] Job 91 queued on 'BJC-600' by 'goh'.
D [12/Oct/2005:00:03:54 +0800] Job 91 hold_until = 0
D [12/Oct/2005:00:03:54 +0800] StartJob(91, 0x80967a8)
D [12/Oct/2005:00:03:54 +0800] StartJob() id = 91, file = 0/1
D [12/Oct/2005:00:03:54 +0800] job-sheets=none,none
D [12/Oct/2005:00:03:54 +0800] banner_page = 0
D [12/Oct/2005:00:03:54 +0800] StartJob: argv = "BJC-600","91","goh","(stdin)","1","Resolution=90x90dpi ProcessColorModel=Greyscale PrintQuality=Draft PrintColors=K BitsPerPixel=1","/var/spool/cups/d00091-001"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[2]="USER=root"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[3]="CHARSET=utf-8"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[4]="LANG=en"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[5]="PPD=/etc/cups/ppd/BJC-600.ppd"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[7]="RIP_MAX_CACHE=8m"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[8]="TMPDIR=/var/spool/cups/tmp"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[9]="CONTENT_TYPE=application/postscript"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[10]="DEVICE_URI=canon:/dev/lp0"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[11]="PRINTER=BJC-600"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[12]="CUPS_DATADIR=/usr/share/cups"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[13]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[14]="CUPS_SERVER=localhost"
D [12/Oct/2005:00:03:54 +0800] StartJob: envp[15]="IPP_PORT=631"
D [12/Oct/2005:00:03:54 +0800] StartJob: statusfds = [ 9 10 ]
D [12/Oct/2005:00:03:54 +0800] StartJob: filterfds[1] = [ 11 -1 ]
D [12/Oct/2005:00:03:54 +0800] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [12/Oct/2005:00:03:54 +0800] StartJob: filterfds[0] = [ 12 13 ]
D [12/Oct/2005:00:03:54 +0800] start_process("/usr/lib/cups/filter/pstops", 0xbffefc50, 0xbffeefc0, 11, 13, 10)
I [12/Oct/2005:00:03:54 +0800] Started filter /usr/lib/cups/filter/pstops (PID 12552) for job 91.
D [12/Oct/2005:00:03:54 +0800] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [12/Oct/2005:00:03:54 +0800] StartJob: filterfds[1] = [ 11 14 ]
D [12/Oct/2005:00:03:54 +0800] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbffefc50, 0xbffeefc0, 12, 14, 10)
I [12/Oct/2005:00:03:54 +0800] Started filter /usr/lib/cups/filter/foomatic-rip (PID 12553) for job 91.
D [12/Oct/2005:00:03:54 +0800] StartJob: backend = "/usr/lib/cups/backend/canon"
D [12/Oct/2005:00:03:54 +0800] StartJob: filterfds[0] = [ -1 12 ]
D [12/Oct/2005:00:03:54 +0800] start_process("/usr/lib/cups/backend/canon", 0xbffefc50, 0xbffeefc0, 11, 12, 10)
I [12/Oct/2005:00:03:54 +0800] Started backend /usr/lib/cups/backend/canon (PID 12554) for job 91.
D [12/Oct/2005:00:03:54 +0800] ProcessIPPRequest: 8 status_code=0
D [12/Oct/2005:00:03:54 +0800] [Job 91] perl: warning: Setting locale failed.
D [12/Oct/2005:00:03:54 +0800] [Job 91] perl: warning: Please check that your locale settings:
D [12/Oct/2005:00:03:54 +0800] [Job 91] LANGUAGE = (unset),
D [12/Oct/2005:00:03:54 +0800] [Job 91] LC_ALL = (unset),
D [12/Oct/2005:00:03:54 +0800] [Job 91] LANG = "en"
D [12/Oct/2005:00:03:54 +0800] [Job 91] are supported and installed on your system.
D [12/Oct/2005:00:03:54 +0800] [Job 91] perl: warning: Falling back to the standard locale ("C").
D [12/Oct/2005:00:03:54 +0800] CloseClient: 8
D [12/Oct/2005:00:03:54 +0800] [Job 91] Page = 595x842; 0,0 to 595,842
D [12/Oct/2005:00:03:54 +0800] [Job 91] slowcollate=0, slowduplex=0, sloworder=0
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BoundingBox: 0 0 594 842
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Qt 3.3.3
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%CreationDate: Wed Oct 12 00:03:54 2005
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Orientation: Landscape
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Pages: 1
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%DocumentFonts: BitstreamVeraSans-Bold TrebuchetMS-Bold TrebuchetMS
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndComments
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginProlog
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndProlog
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [12/Oct/2005:00:03:54 +0800] [Job 91] Parsing PPD file ...
D [12/Oct/2005:00:03:54 +0800] [Job 91] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option ColorSpace
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option PageSize
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option PageRegion
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option ImageableArea
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option PaperDimension
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option Manual
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option MediaType
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option MediaWeight
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option Resolution
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option PrintQuality
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option BitsPerPixel
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option Monochrome
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option ProcessColorModel
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option PrintColors
D [12/Oct/2005:00:03:54 +0800] [Job 91] Added option Font
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Parameter Summary
D [12/Oct/2005:00:03:54 +0800] [Job 91] -----------------
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Spooler: cups
D [12/Oct/2005:00:03:54 +0800] [Job 91] Printer: BJC-600
D [12/Oct/2005:00:03:54 +0800] [Job 91] PPD file: /etc/cups/ppd/BJC-600.ppd
D [12/Oct/2005:00:03:54 +0800] [Job 91] Printer model: Canon BJC-600 Foomatic/bjc600 (recommended)
D [12/Oct/2005:00:03:54 +0800] [Job 91] Job title: stdin
D [12/Oct/2005:00:03:54 +0800] [Job 91] File(s) to be printed: 
D [12/Oct/2005:00:03:54 +0800] [Job 91] <STDIN>
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Pondering option 'Resolution=90x90dpi'
D [12/Oct/2005:00:03:54 +0800] [Job 91] Pondering option 'ProcessColorModel=Greyscale'
D [12/Oct/2005:00:03:54 +0800] [Job 91] Pondering option 'PrintQuality=Draft'
D [12/Oct/2005:00:03:54 +0800] [Job 91] Pondering option 'PrintColors=K'
D [12/Oct/2005:00:03:54 +0800] [Job 91] Pondering option 'BitsPerPixel=1'
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] ================================================
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] File: <STDIN>
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] ================================================
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Reading PostScript input ...
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginFont: Trebuchet MS Bold
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Copyright: Copyright (c) 1996 Microsoft Corporation. All rights reserved.
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Converted from TrueType by Qt
D [12/Oct/2005:00:03:54 +0800] [Job 91] --> This document is DSC-conforming!
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] -----------
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginProlog
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%EndProlog
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] -----------
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] Inserting PostScript code for CUPS' page accounting
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *Monochrome False
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: Monochrome=False --> Correcting numerical/string option to Monochrome=0 (Command line argument)
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *ProcessColorModel Greyscale
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: ProcessColorModel=Greyscale --> Setting option
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %% FoomaticRIPOptionSetting: ProcessColorModel=Greyscale
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: ProcessColorModel=Greyscale --> Setting option
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *BitsPerPixel 1
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: BitsPerPixel=1 --> Setting option
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %% FoomaticRIPOptionSetting: BitsPerPixel=1
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: BitsPerPixel=1 --> Setting option
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *MediaType plain
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: MediaType=plain --> Option will be set by PostScript interpreter
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *MediaWeight Normal
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: MediaWeight=Normal --> Option will be set by PostScript interpreter
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *PageSize A4
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: PageSize=A4 --> Option will be set by PostScript interpreter
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *PrintQuality Draft
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: PrintQuality=Draft --> Option will be set by PostScript interpreter
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *Manual False
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: Manual=False --> Correcting numerical/string option to Manual=0 (Command line argument)
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *PrintColors K
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: PrintColors=K --> Option will be set by PostScript interpreter
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginFeature: *Resolution 90x90dpi
D [12/Oct/2005:00:03:54 +0800] [Job 91] Option: Resolution=90x90dpi --> Option will be set by PostScript interpreter
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %% Font Page 00
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginFont: TrebuchetMS-Bold
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%FontName: TrebuchetMS-Bold-Uni
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Composite font created by Qt
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndFont
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndFont
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginFont: Bitstream Vera Sans Bold
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Copyright: Copyright (c) 2003 by Bitstream, Inc. All Rights Reserved.
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Converted from TrueType by Qt
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %% Font Page 00
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginFont: BitstreamVeraSans-Bold
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%FontName: BitstreamVeraSans-Bold-Uni
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Composite font created by Qt
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndFont
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndFont
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginFont: Trebuchet MS
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Copyright: Copyright (c) 1996 Microsoft Corporation. All rights reserved.
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Converted from TrueType by Qt
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %% Font Page 00
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginFont: TrebuchetMS
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%FontName: TrebuchetMS-Uni
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Creator: Composite font created by Qt
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndFont
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndFont
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Page: 1 1
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Page: 1 1
D [12/Oct/2005:00:03:54 +0800] [Job 91] pw = 595.0, pl = 842.0
D [12/Oct/2005:00:03:54 +0800] [Job 91] PageLeft = 0.0, PageRight = 595.0
D [12/Oct/2005:00:03:54 +0800] [Job 91] PageTop = 842.0, PageBottom = 0.0
D [12/Oct/2005:00:03:54 +0800] [Job 91] PageWidth = 595.0, PageLength = 842.0
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%BeginPageSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%EndPageSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] 0 %%Trailer
D [12/Oct/2005:00:03:54 +0800] [Job 91] Saw Trailer!
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%EndSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] -----------
D [12/Oct/2005:00:03:54 +0800] [Job 91] New page:  1 1
D [12/Oct/2005:00:03:54 +0800] [Job 91] Inserting option code into "PageSetup" section.
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%BeginPageSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found: %%EndPageSetup
D [12/Oct/2005:00:03:54 +0800] [Job 91] End of page header
D [12/Oct/2005:00:03:54 +0800] [Job 91] Saw EOF!
D [12/Oct/2005:00:03:54 +0800] [Job 91] Stopping search for page header options
D [12/Oct/2005:00:03:54 +0800] [Job 91] Found:
D [12/Oct/2005:00:03:54 +0800] [Job 91] <00090002>[9 0 0 0]18 578 XYT
D [12/Oct/2005:00:03:54 +0800] [Job 91] --> Output goes directly to the renderer now.
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Starting renderer
D [12/Oct/2005:00:03:54 +0800] [Job 91] JCL: <job data> 
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] renderer PID kid4=12556
D [12/Oct/2005:00:03:54 +0800] [Job 91] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=bjc600 -dBitsPerPixel=1 -dProcessColorModel=/DeviceGray -sOutputFile=- -
D [12/Oct/2005:00:03:54 +0800] [Job 91] perl: warning: Setting locale failed.
D [12/Oct/2005:00:03:54 +0800] [Job 91] perl: warning: Please check that your locale settings:
D [12/Oct/2005:00:03:54 +0800] [Job 91] LANGUAGE = (unset),
D [12/Oct/2005:00:03:54 +0800] [Job 91] LC_ALL = (unset),
D [12/Oct/2005:00:03:54 +0800] [Job 91] LANG = "en"
D [12/Oct/2005:00:03:54 +0800] [Job 91] are supported and installed on your system.
D [12/Oct/2005:00:03:54 +0800] [Job 91] perl: warning: Falling back to the standard locale ("C").
D [12/Oct/2005:00:03:54 +0800] [Job 91] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=bjc600' '-dBitsPerPixel=1' '-dProcessColorModel=/DeviceGray' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [12/Oct/2005:00:03:54 +0800] ReadClient: 6 POST / HTTP/1.1
D [12/Oct/2005:00:03:54 +0800] ProcessIPPRequest: 6 status_code=0
D [12/Oct/2005:00:03:54 +0800] [Job 91] 
D [12/Oct/2005:00:03:54 +0800] [Job 91] Closing renderer
W [12/Oct/2005:00:03:54 +0800] [Job 91] Received 35 bytes of unknown back-channel data!
D [12/Oct/2005:00:03:55 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:03:55 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:03:56 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:03:56 +0800] ProcessIPPRequest: 5 status_code=0
D [12/Oct/2005:00:03:56 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:03:56 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:03:56 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:03:56 +0800] ProcessIPPRequest: 5 status_code=1
D [12/Oct/2005:00:03:56 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:03:56 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:03:58 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:03:58 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:03:58 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:03:58 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:03:58 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:03:58 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:03:59 +0800] ReadClient: 6 POST / HTTP/1.1
D [12/Oct/2005:00:03:59 +0800] ProcessIPPRequest: 6 status_code=0
D [12/Oct/2005:00:04:01 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:01 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:01 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:01 +0800] ProcessIPPRequest: 5 status_code=0
D [12/Oct/2005:00:04:01 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:01 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:01 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:01 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:04:01 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:01 +0800] ProcessIPPRequest: 5 status_code=1
D [12/Oct/2005:00:04:04 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:04 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:04 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:04 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:04:04 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:04 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:04 +0800] ReadClient: 6 POST / HTTP/1.1
D [12/Oct/2005:00:04:04 +0800] ProcessIPPRequest: 6 status_code=0
W [12/Oct/2005:00:04:05 +0800] [Job 91] Received 35 bytes of unknown back-channel data!
D [12/Oct/2005:00:04:06 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:06 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:06 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:06 +0800] ProcessIPPRequest: 5 status_code=0
D [12/Oct/2005:00:04:06 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:06 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:04:06 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:06 +0800] ProcessIPPRequest: 5 status_code=1
D [12/Oct/2005:00:04:07 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:07 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:09 +0800] ReadClient: 6 POST / HTTP/1.1
D [12/Oct/2005:00:04:09 +0800] ProcessIPPRequest: 6 status_code=0
D [12/Oct/2005:00:04:10 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:10 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:10 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:10 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:04:10 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:10 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:11 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:11 +0800] ProcessIPPRequest: 5 status_code=0
D [12/Oct/2005:00:04:11 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:11 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:11 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:11 +0800] ProcessIPPRequest: 5 status_code=1
D [12/Oct/2005:00:04:11 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:11 +0800] ProcessIPPRequest: 7 status_code=1
D [12/Oct/2005:00:04:13 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:13 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:14 +0800] ReadClient: 6 POST / HTTP/1.1
D [12/Oct/2005:00:04:14 +0800] ProcessIPPRequest: 6 status_code=0
W [12/Oct/2005:00:04:15 +0800] [Job 91] Received 35 bytes of unknown back-channel data!
W [12/Oct/2005:00:04:15 +0800] [Job 91] Received 35 bytes of unknown back-channel data!
D [12/Oct/2005:00:04:15 +0800] [Job 91] KID3 exited with status 0
W [12/Oct/2005:00:04:15 +0800] [Job 91] Received 35 bytes of unknown back-channel data!
D [12/Oct/2005:00:04:15 +0800] [Job 91] tail process done writing data to STDOUT
D [12/Oct/2005:00:04:15 +0800] [Job 91] KID4 finished
D [12/Oct/2005:00:04:15 +0800] [Job 91] KID4 exited with status 0
D [12/Oct/2005:00:04:15 +0800] [Job 91] Renderer exit stat: 0
D [12/Oct/2005:00:04:15 +0800] [Job 91] KID3 finished
D [12/Oct/2005:00:04:15 +0800] [Job 91] Renderer process finished
D [12/Oct/2005:00:04:15 +0800] [Job 91] 
D [12/Oct/2005:00:04:15 +0800] [Job 91] Closing foomatic-rip.
W [12/Oct/2005:00:04:15 +0800] [Job 91] Received 35 bytes of unknown back-channel data!
D [12/Oct/2005:00:04:16 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:16 +0800] ProcessIPPRequest: 5 status_code=0
D [12/Oct/2005:00:04:16 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:16 +0800] ProcessIPPRequest: 7 status_code=0
D [12/Oct/2005:00:04:16 +0800] UpdateJob: job 91, file 0 is complete.
D [12/Oct/2005:00:04:16 +0800] CancelJob: id = 91
D [12/Oct/2005:00:04:16 +0800] StopJob: id = 91, force = 0
D [12/Oct/2005:00:04:16 +0800] StopJob: printer state is 3
D [12/Oct/2005:00:04:16 +0800] ReadClient: 5 POST / HTTP/1.1
D [12/Oct/2005:00:04:16 +0800] ProcessIPPRequest: 5 status_code=1
D [12/Oct/2005:00:04:16 +0800] ReadClient: 7 POST / HTTP/1.1
D [12/Oct/2005:00:04:16 +0800] ProcessIPPRequest: 7 status_code=1

---


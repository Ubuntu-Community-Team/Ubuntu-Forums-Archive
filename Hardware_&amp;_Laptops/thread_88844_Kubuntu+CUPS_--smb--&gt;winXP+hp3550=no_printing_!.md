---
title: "Kubuntu+CUPS --smb--&gt;winXP+hp3550=no printing !!"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by nama4ever on 2005-11-11
Hi everybody.... here's my problem:

My Laptop + Kubuntu Breezy+ Cups would like to print on the hp3550 connected to my desktop machine running WinXP through a SMB REMOTE QUEUE.

My Samba configuration seems ok: everything is shared in the right way, and I can access from both computers to my shard folders.

I configured the remote printer using the Kde Wizard: when printing to the device the job  gets to winxp, but then sits there and hangs. Only a reboot of my mother's desktop can empty the remote queue. The job seems interrupted after a 64k transfer.

Can you solve it ???

Thanx in advance !!
Nanni


Here are the logs:

PRINTER TEST
print_job: auto-typing file...
D [11/Nov/2005:13:21:30 +0100] print_job: request file type is application/postscript.
D [11/Nov/2005:13:21:30 +0100] check_quotas: requesting-user-name = 'root'
D [11/Nov/2005:13:21:30 +0100] print_job: requesting-user-name = 'root'
D [11/Nov/2005:13:21:30 +0100] Adding default job-sheets values "none,none"...
I [11/Nov/2005:13:21:30 +0100] Adding start banner page "none" to job 8.
I [11/Nov/2005:13:21:30 +0100] Adding end banner page "none" to job 8.
I [11/Nov/2005:13:21:30 +0100] Job 8 queued on 'hp3550' by 'root'.
D [11/Nov/2005:13:21:30 +0100] Job 8 hold_until = 0
D [11/Nov/2005:13:21:30 +0100] StartJob(8, 0x8096568)
D [11/Nov/2005:13:21:30 +0100] StartJob() id = 8, file = 0/1
D [11/Nov/2005:13:21:30 +0100] job-sheets=none,none
D [11/Nov/2005:13:21:30 +0100] banner_page = 0
D [11/Nov/2005:13:21:30 +0100] StartJob: argv = "hp3550","8","root","KDE Print Test","1","multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3","/var/spool/cups/d00008-001"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[2]="USER=root"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[3]="CHARSET=utf-8"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[4]="LANG=it"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[5]="TZ=Europe/Rome"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[6]="PPD=/etc/cups/ppd/hp3550.ppd"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[11]="DEVICE_URI=smb://tigrosnet/192.168.0.1/hp3550"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[12]="PRINTER=hp3550"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[15]="CUPS_SERVER=localhost"
D [11/Nov/2005:13:21:30 +0100] StartJob: envp[16]="IPP_PORT=631"
D [11/Nov/2005:13:21:30 +0100] StartJob: statusfds = [ 6 7 ]
D [11/Nov/2005:13:21:30 +0100] StartJob: filterfds[1] = [ 8 -1 ]
D [11/Nov/2005:13:21:30 +0100] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [11/Nov/2005:13:21:30 +0100] StartJob: filterfds[0] = [ 9 10 ]
D [11/Nov/2005:13:21:30 +0100] start_process("/usr/lib/cups/filter/pstops", 0xbfbf70a0, 0xbfbf6618, 8, 10, 7)
I [11/Nov/2005:13:21:30 +0100] Started filter /usr/lib/cups/filter/pstops (PID 25775) for job 8.
D [11/Nov/2005:13:21:30 +0100] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [11/Nov/2005:13:21:30 +0100] StartJob: filterfds[1] = [ 8 11 ]
D [11/Nov/2005:13:21:30 +0100] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbfbf70a0, 0xbfbf6618, 9, 11, 7)
I [11/Nov/2005:13:21:30 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 25776) for job 8.
D [11/Nov/2005:13:21:30 +0100] StartJob: backend = "/usr/lib/cups/backend/smb"
D [11/Nov/2005:13:21:30 +0100] StartJob: filterfds[0] = [ -1 9 ]
D [11/Nov/2005:13:21:30 +0100] start_process("/usr/lib/cups/backend/smb", 0xbfbf70a0, 0xbfbf6618, 8, 9, 7)
I [11/Nov/2005:13:21:30 +0100] Started backend /usr/lib/cups/backend/smb (PID 25777) for job 8.
D [11/Nov/2005:13:21:30 +0100] ProcessIPPRequest: 4 status_code=0
D [11/Nov/2005:13:21:30 +0100] [Job 8] Page = 595x842; 10,36 to 585,833
D [11/Nov/2005:13:21:30 +0100] [Job 8] slowcollate=0, slowduplex=0, sloworder=0
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%BoundingBox: 0 0 612 792
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%Pages: 1
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%LanguageLevel: 1
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%DocumentData: Clean7Bit
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%DocumentSuppliedResources: procset testprint/1.0
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%DocumentNeededResources: font Helvetica Helvetica-Bold Times-Roman
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%Creator: Michael Sweet, Easy Software Products
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%CreationDate: May 11, 1999
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%Title: Test Page
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%EndComments
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%BeginProlog
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%BeginResource procset testprint 1.1 0
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%EndResource
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%EndProlog
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%Page: 1 1
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%Page: 1 1
D [11/Nov/2005:13:21:30 +0100] [Job 8] pw = 575.6, pl = 797.0
D [11/Nov/2005:13:21:30 +0100] [Job 8] PageLeft = 9.7, PageRight = 585.3
D [11/Nov/2005:13:21:30 +0100] [Job 8] PageTop = 833.0, PageBottom = 36.0
D [11/Nov/2005:13:21:30 +0100] [Job 8] PageWidth = 595.0, PageLength = 842.0
D [11/Nov/2005:13:21:30 +0100] [Job 8] 0 %%EOF
D [11/Nov/2005:13:21:30 +0100] [Job 8] Saw EOF!
D [11/Nov/2005:13:21:30 +0100] [Job 8] perl: warning: Setting locale failed.
D [11/Nov/2005:13:21:30 +0100] [Job 8] perl: warning: Please check that your locale settings:
D [11/Nov/2005:13:21:30 +0100] [Job 8] LANGUAGE = (unset),
D [11/Nov/2005:13:21:30 +0100] [Job 8] LC_ALL = (unset),
D [11/Nov/2005:13:21:30 +0100] [Job 8] LANG = "it"
D [11/Nov/2005:13:21:30 +0100] [Job 8] are supported and installed on your system.
D [11/Nov/2005:13:21:30 +0100] [Job 8] perl: warning: Falling back to the standard locale ("C").
D [11/Nov/2005:13:21:30 +0100] CloseClient: 4
D [11/Nov/2005:13:21:30 +0100] [Job 8] foomatic-rip version $Revision: 3.43.2.11 $ running...
D [11/Nov/2005:13:21:30 +0100] [Job 8] Parsing PPD file ...
D [11/Nov/2005:13:21:30 +0100] [Job 8] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option ColorSpace
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option Resolution
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option PageSize
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option PageRegion
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option Model
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option PrintoutMode
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option ImageableArea
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option PaperDimension
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option Quality
D [11/Nov/2005:13:21:30 +0100] [Job 8] Added option Font
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] Parameter Summary
D [11/Nov/2005:13:21:30 +0100] [Job 8] -----------------
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] Spooler: cups
D [11/Nov/2005:13:21:30 +0100] [Job 8] Printer: hp3550
D [11/Nov/2005:13:21:30 +0100] [Job 8] PPD file: /etc/cups/ppd/hp3550.ppd
D [11/Nov/2005:13:21:30 +0100] [Job 8] Printer model: HP DeskJet 3550 Foomatic/hpijs (recommended)
D [11/Nov/2005:13:21:30 +0100] [Job 8] Job title: KDE Print Test
D [11/Nov/2005:13:21:30 +0100] [Job 8] File(s) to be printed:
D [11/Nov/2005:13:21:30 +0100] [Job 8] <STDIN>
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [11/Nov/2005:13:21:30 +0100] [Job 8] Pondering option 'multiple-document-handling=separate-documents-uncollated-copies'
D [11/Nov/2005:13:21:30 +0100] [Job 8] Unknown option multiple-document-handling=separate-documents-uncollated-copies.
D [11/Nov/2005:13:21:30 +0100] [Job 8] Pondering option 'orientation-requested=3'
D [11/Nov/2005:13:21:30 +0100] [Job 8] Unknown option orientation-requested=3.
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] ================================================
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] File: <STDIN>
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] ================================================
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] Reading PostScript input ...
D [11/Nov/2005:13:21:30 +0100] [Job 8] --> This document is DSC-conforming!
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] -----------
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%BeginProlog
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%EndProlog
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] -----------
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%BeginSetup
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%BeginFeature: *PrintoutMode Normal
D [11/Nov/2005:13:21:30 +0100] [Job 8] Option: PrintoutMode=Normal --> Setting option
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [11/Nov/2005:13:21:30 +0100] [Job 8] Option: PrintoutMode=Normal --> Setting option
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%BeginFeature: *Quality FromPrintoutMode
D [11/Nov/2005:13:21:30 +0100] [Job 8] Option: Quality=FromPrintoutMode --> Setting option
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [11/Nov/2005:13:21:30 +0100] [Job 8] Option: Quality=FromPrintoutMode --> Setting option
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%BeginFeature: *PageSize A4
D [11/Nov/2005:13:21:30 +0100] [Job 8] Option: PageSize=A4 --> Setting option
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [11/Nov/2005:13:21:30 +0100] [Job 8] Option: PageSize=A4 --> Setting option
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found: %%EndSetup
D [11/Nov/2005:13:21:30 +0100] [Job 8] Inserting PostScript code for CUPS' page accounting
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] -----------
D [11/Nov/2005:13:21:30 +0100] [Job 8] New page:  1 1
D [11/Nov/2005:13:21:30 +0100] [Job 8] Inserting option code into "PageSetup" section.
D [11/Nov/2005:13:21:30 +0100] [Job 8] No page header or page header not DSC-conforming
D [11/Nov/2005:13:21:30 +0100] [Job 8] Stopping search for page header options
D [11/Nov/2005:13:21:30 +0100] [Job 8] Found:
D [11/Nov/2005:13:21:30 +0100] [Job 8] pageHeight sub                   % Move down...
D [11/Nov/2005:13:21:30 +0100] [Job 8] --> Output goes directly to the renderer now.
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] Starting renderer
D [11/Nov/2005:13:21:30 +0100] [Job 8] JCL: <job data>
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] renderer PID kid4=25779
D [11/Nov/2005:13:21:30 +0100] [Job 8] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 3320" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1 -dIjsUseOutputFD -sOutputFile=- -
D [11/Nov/2005:13:21:30 +0100] [Job 8] perl: warning: Setting locale failed.
D [11/Nov/2005:13:21:30 +0100] [Job 8] perl: warning: Please check that your locale settings:
D [11/Nov/2005:13:21:30 +0100] [Job 8] LANGUAGE = (unset),
D [11/Nov/2005:13:21:30 +0100] [Job 8] LC_ALL = (unset),
D [11/Nov/2005:13:21:30 +0100] [Job 8] LANG = "it"
D [11/Nov/2005:13:21:30 +0100] [Job 8] are supported and installed on your system.
D [11/Nov/2005:13:21:30 +0100] [Job 8] perl: warning: Falling back to the standard locale ("C").
D [11/Nov/2005:13:21:30 +0100] [Job 8] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 3320' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [11/Nov/2005:13:21:30 +0100] [Job 8]
D [11/Nov/2005:13:21:30 +0100] [Job 8] Closing renderer
D [11/Nov/2005:13:21:39 +0100] [Job 8] KID3 exited with status 0
D [11/Nov/2005:13:21:39 +0100] [Job 8] tail process done writing data to STDOUT
D [11/Nov/2005:13:21:39 +0100] [Job 8] KID4 finished
D [11/Nov/2005:13:21:39 +0100] [Job 8] KID4 exited with status 0
D [11/Nov/2005:13:21:39 +0100] [Job 8] Renderer exit stat: 0
D [11/Nov/2005:13:21:39 +0100] [Job 8] KID3 finished
D [11/Nov/2005:13:21:39 +0100] [Job 8] Renderer process finished
D [11/Nov/2005:13:21:39 +0100] [Job 8]
D [11/Nov/2005:13:21:39 +0100] [Job 8] Closing foomatic-rip.
D [11/Nov/2005:13:21:39 +0100] UpdateJob: job 8, file 0 is complete.
D [11/Nov/2005:13:21:39 +0100] CancelJob: id = 8
D [11/Nov/2005:13:21:39 +0100] StopJob: id = 8, force = 0
D [11/Nov/2005:13:21:39 +0100] StopJob: printer state is 3

---


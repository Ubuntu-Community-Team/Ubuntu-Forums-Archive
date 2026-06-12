---
title: "HP laserjet 3p trouble"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by dieselpower on 2005-09-01
I have a laserjet 3p with pcl5 (whatever that is?) that I cannot make work corectly. It will print with the "laserjet 3P W/pcl5 ljet4" driver but photo quality is bad. The "laserjet 3P W/pcl5" driver that I used to use with debian always cancels the print job. here is the error log.


I [01/Sep/2005:11:44:04 -0500] Listening to 7f000001:631
D [01/Sep/2005:11:44:04 -0500] AddLocation: added location '/'
D [01/Sep/2005:11:44:04 -0500] DenyIP: / deny 00000000/00000000
D [01/Sep/2005:11:44:04 -0500] AllowIP: / allow 7f000001/ffffffff
D [01/Sep/2005:11:44:04 -0500] AddLocation: added location '/jobs'
D [01/Sep/2005:11:44:04 -0500] AddLocation: added location '/admin'
D [01/Sep/2005:11:44:04 -0500] DenyIP: /admin deny 00000000/00000000
D [01/Sep/2005:11:44:04 -0500] AllowIP: /admin allow 7f000001/ffffffff
I [01/Sep/2005:11:44:04 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [01/Sep/2005:11:44:04 -0500] Configured for up to 100 clients.
I [01/Sep/2005:11:44:04 -0500] Allowing up to 100 client connections per host.
I [01/Sep/2005:11:44:04 -0500] Full reload is required.
D [01/Sep/2005:11:44:04 -0500] LoadAllPrinters: Loading printer Laserjet3p...
D [01/Sep/2005:11:44:04 -0500] LoadDevices: Added device "ipp"...
D [01/Sep/2005:11:44:04 -0500] LoadDevices: Added device "lpd"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "smb"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp0"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp1"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp2"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp3"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp4"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp5"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp6"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp7"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp8"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp9"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp10"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp11"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp12"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp13"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp14"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "usb:/dev/usb/lp15"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "http"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "canon:/dev/lp0"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "epson:/dev/lp0"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "parallel:/dev/lp0"...
D [01/Sep/2005:11:44:05 -0500] LoadDevices: Added device "socket"...
I [01/Sep/2005:11:44:05 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [01/Sep/2005:11:44:06 -0500] LoadPPDs: No new or changed PPDs...
D [01/Sep/2005:11:44:06 -0500] LoadAllJobs: Scanning /var/spool/cups...
D [01/Sep/2005:11:44:06 -0500] LoadAllJobs: Loading attributes for job 4...
D [01/Sep/2005:11:44:06 -0500] LoadAllJobs: Loading attributes for job 8...
D [01/Sep/2005:11:44:06 -0500] LoadAllJobs: Loading attributes for job 9...
I [01/Sep/2005:11:44:06 -0500] Full reload complete.
D [01/Sep/2005:11:44:06 -0500] StartListening: NumListeners=1
D [01/Sep/2005:11:44:06 -0500] StartListening: address=7f000001 port=631
D [01/Sep/2005:11:44:06 -0500] ResumeListening: setting input bits...
D [01/Sep/2005:11:46:41 -0500] AcceptClient: 4 from localhost:631.
D [01/Sep/2005:11:46:41 -0500] ReadClient: 4 POST / HTTP/1.1
D [01/Sep/2005:11:46:41 -0500] ProcessIPPRequest: 4 status_code=1
D [01/Sep/2005:11:46:41 -0500] ReadClient: 4 POST / HTTP/1.1
D [01/Sep/2005:11:46:41 -0500] ProcessIPPRequest: 4 status_code=1
D [01/Sep/2005:11:46:41 -0500] ReadClient: 4 POST / HTTP/1.1
D [01/Sep/2005:11:46:41 -0500] ProcessIPPRequest: 4 status_code=0
D [01/Sep/2005:11:46:41 -0500] CloseClient: 4
D [01/Sep/2005:11:46:41 -0500] AcceptClient: 4 from localhost:631.
D [01/Sep/2005:11:46:41 -0500] ReadClient: 4 POST / HTTP/1.1
D [01/Sep/2005:11:46:41 -0500] ProcessIPPRequest: 4 status_code=0
D [01/Sep/2005:11:46:41 -0500] ReadClient: 4 GET /printers/Laserjet3p.ppd HTTP/1.1
D [01/Sep/2005:11:46:41 -0500] SendFile: 4 file=5
D [01/Sep/2005:11:47:01 -0500] ReadClient: 4 POST /printers/Laserjet3p HTTP/1.1
D [01/Sep/2005:11:47:02 -0500] print_job: auto-typing file...
D [01/Sep/2005:11:47:02 -0500] print_job: request file type is application/postscript.
D [01/Sep/2005:11:47:02 -0500] check_quotas: requesting-user-name = 'lawrence'
D [01/Sep/2005:11:47:02 -0500] print_job: requesting-user-name = 'lawrence'
D [01/Sep/2005:11:47:02 -0500] Adding default job-sheets values "none,none"...
I [01/Sep/2005:11:47:02 -0500] Adding start banner page "none" to job 10.
I [01/Sep/2005:11:47:02 -0500] Adding end banner page "none" to job 10.
I [01/Sep/2005:11:47:02 -0500] Job 10 queued on 'Laserjet3p' by 'lawrence'.
D [01/Sep/2005:11:47:02 -0500] Job 10 hold_until = 0
D [01/Sep/2005:11:47:02 -0500] StartJob(10, 0x8096030)
D [01/Sep/2005:11:47:02 -0500] StartJob() id = 10, file = 0/1
D [01/Sep/2005:11:47:02 -0500] job-sheets=none,none
D [01/Sep/2005:11:47:02 -0500] banner_page = 0
D [01/Sep/2005:11:47:02 -0500] StartJob: argv = "Laserjet3p","10","lawrence","pics.sxw","1","","/var/spool/cups/d00010-001"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[2]="USER=root"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[3]="CHARSET=utf-8"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[4]="LANG=en_US"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[5]="TZ=US/Central"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[6]="PPD=/etc/cups/ppd/Laserjet3p.ppd"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[11]="DEVICE_URI=parallel:/dev/lp0"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[12]="PRINTER=Laserjet3p"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[15]="CUPS_SERVER=localhost"
D [01/Sep/2005:11:47:02 -0500] StartJob: envp[16]="IPP_PORT=631"
D [01/Sep/2005:11:47:02 -0500] StartJob: statusfds = [ 5 6 ]
D [01/Sep/2005:11:47:02 -0500] StartJob: filterfds[1] = [ 7 -1 ]
D [01/Sep/2005:11:47:02 -0500] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [01/Sep/2005:11:47:02 -0500] StartJob: filterfds[0] = [ 8 9 ]
D [01/Sep/2005:11:47:02 -0500] start_process("/usr/lib/cups/filter/pstops", 0xbfff0140, 0xbffef4b0, 7, 9, 6)
I [01/Sep/2005:11:47:02 -0500] Started filter /usr/lib/cups/filter/pstops (PID 7295) for job 10.
D [01/Sep/2005:11:47:02 -0500] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [01/Sep/2005:11:47:02 -0500] StartJob: filterfds[1] = [ 7 10 ]
D [01/Sep/2005:11:47:02 -0500] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbfff0140, 0xbffef4b0, 8, 10, 6)
I [01/Sep/2005:11:47:02 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7296) for job 10.
D [01/Sep/2005:11:47:02 -0500] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [01/Sep/2005:11:47:02 -0500] StartJob: filterfds[0] = [ -1 8 ]
D [01/Sep/2005:11:47:02 -0500] start_process("/usr/lib/cups/backend/parallel", 0xbfff0140, 0xbffef4b0, 7, 8, 6)
I [01/Sep/2005:11:47:02 -0500] Started backend /usr/lib/cups/backend/parallel (PID 7297) for job 10.
D [01/Sep/2005:11:47:02 -0500] ProcessIPPRequest: 4 status_code=0
D [01/Sep/2005:11:47:02 -0500] [Job 10] Page = 612x792; 0,0 to 612,792
D [01/Sep/2005:11:47:02 -0500] [Job 10] slowcollate=0, slowduplex=0, sloworder=0
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%BoundingBox: (atend)
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%Creator: OpenOffice.org 1.1.3
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%For: lawrence
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%CreationDate: Thu Sep  1 11:46:59 2005
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%Title: pics.sxw
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%LanguageLevel: 3
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%DocumentData: Clean7Bit
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%Pages: (atend)
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%PageOrder: Ascend
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%EndComments
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%BeginProlog
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%BeginResource: procset PSPrint-Prolog 1.0 0
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%EndResource
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%EndProlog
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%BeginSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%EndSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%Page: 1 1
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%Page: 1 1
D [01/Sep/2005:11:47:02 -0500] [Job 10] pw = 612.0, pl = 792.0
D [01/Sep/2005:11:47:02 -0500] [Job 10] PageLeft = 0.0, PageRight = 612.0
D [01/Sep/2005:11:47:02 -0500] [Job 10] PageTop = 792.0, PageBottom = 0.0
D [01/Sep/2005:11:47:02 -0500] [Job 10] PageWidth = 612.0, PageLength = 792.0
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%PageBoundingBox: 0 0 612 792
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%BeginPageSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%BeginFeature: *PageSize Letter
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%EndFeature
D [01/Sep/2005:11:47:02 -0500] [Job 10] 0 %%EndPageSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] perl: warning: Setting locale failed.
D [01/Sep/2005:11:47:02 -0500] [Job 10] perl: warning: Please check that your locale settings:
D [01/Sep/2005:11:47:02 -0500] [Job 10] LANGUAGE = (unset),
D [01/Sep/2005:11:47:02 -0500] [Job 10] LC_ALL = (unset),
D [01/Sep/2005:11:47:02 -0500] [Job 10] LANG = "en_US"
D [01/Sep/2005:11:47:02 -0500] [Job 10] are supported and installed on your system.
D [01/Sep/2005:11:47:02 -0500] [Job 10] perl: warning: Falling back to the standard locale ("C").
D [01/Sep/2005:11:47:02 -0500] [Job 10] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [01/Sep/2005:11:47:02 -0500] [Job 10] Parsing PPD file ...
D [01/Sep/2005:11:47:02 -0500] [Job 10] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [01/Sep/2005:11:47:02 -0500] [Job 10] Added option ColorSpace
D [01/Sep/2005:11:47:02 -0500] [Job 10] Added option PageSize
D [01/Sep/2005:11:47:02 -0500] [Job 10] Added option PageRegion
D [01/Sep/2005:11:47:02 -0500] [Job 10] Added option ImageableArea
D [01/Sep/2005:11:47:02 -0500] [Job 10] Added option PaperDimension
D [01/Sep/2005:11:47:02 -0500] [Job 10] Added option Font
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] Parameter Summary
D [01/Sep/2005:11:47:02 -0500] [Job 10] -----------------
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] Spooler: cups
D [01/Sep/2005:11:47:02 -0500] [Job 10] Printer: Laserjet3p
D [01/Sep/2005:11:47:02 -0500] [Job 10] PPD file: /etc/cups/ppd/Laserjet3p.ppd
D [01/Sep/2005:11:47:02 -0500] [Job 10] Printer model: HP LaserJet 3P w/ PCL5 Foomatic/gimp-print (recommended)
D [01/Sep/2005:11:47:02 -0500] [Job 10] Job title: pics.sxw
D [01/Sep/2005:11:47:02 -0500] [Job 10] File(s) to be printed: 
D [01/Sep/2005:11:47:02 -0500] [Job 10] <STDIN>
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] ================================================
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] File: <STDIN>
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] ================================================
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] Reading PostScript input ...
D [01/Sep/2005:11:47:02 -0500] [Job 10] --> This document is DSC-conforming!
D [01/Sep/2005:11:47:02 -0500] [Job 10] Document created with OpenOffice.org 1.1.x
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%BeginProlog
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%EndProlog
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%BeginSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] Inserting PostScript code for CUPS' page accounting
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%BeginFeature: *PageSize Letter
D [01/Sep/2005:11:47:02 -0500] [Job 10] Option: PageSize=Letter --> Option will be set by PostScript interpreter
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%EndSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:02 -0500] [Job 10] New page:  1 1
D [01/Sep/2005:11:47:02 -0500] [Job 10] Inserting option code into "PageSetup" section.
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%BeginPageSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%BeginFeature: *PageSize Letter
D [01/Sep/2005:11:47:02 -0500] [Job 10] Option: PageSize=Letter --> Option will be set by PostScript interpreter
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found: %%EndPageSetup
D [01/Sep/2005:11:47:02 -0500] [Job 10] End of page header
D [01/Sep/2005:11:47:02 -0500] [Job 10] Stopping search for page header options
D [01/Sep/2005:11:47:02 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:02 -0500] [Job 10] -MM8J;Qj0U*C@oiA(^;GML-\:E+Ml0oTj&%#f^=,TF2JA2!SO#PR6Fa\U;bE59\HHV(/`^\R)Jl$ml>c
D [01/Sep/2005:11:47:02 -0500] [Job 10] --> Output goes directly to the renderer now.
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] Starting renderer
D [01/Sep/2005:11:47:02 -0500] [Job 10] JCL: <job data> 
D [01/Sep/2005:11:47:02 -0500] [Job 10] 
D [01/Sep/2005:11:47:02 -0500] [Job 10] renderer PID kid4=7300
D [01/Sep/2005:11:47:02 -0500] [Job 10] renderer command: 
D [01/Sep/2005:11:47:02 -0500] [Job 10] renderer return value: 255
D [01/Sep/2005:11:47:02 -0500] [Job 10] renderer received signal: 255
D [01/Sep/2005:11:47:03 -0500] [Job 10] tail process done writing data to STDOUT
D [01/Sep/2005:11:47:03 -0500] [Job 10] KID4 finished
D [01/Sep/2005:11:47:03 -0500] [Job 10] Process dying with "The renderer command line returned an unrecognized error code 255.", exit stat: 1
D [01/Sep/2005:11:47:03 -0500] [Job 10] The renderer command line returned an unrecognized error code 255.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%PageTrailer
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%Page: 2 2
D [01/Sep/2005:11:47:03 -0500] [Job 10] pw = 612.0, pl = 792.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageLeft = 0.0, PageRight = 612.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageTop = 792.0, PageBottom = 0.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageWidth = 612.0, PageLength = 792.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%PageBoundingBox: 0 0 612 792
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%BeginPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%EndPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:03 -0500] [Job 10] New page:  2 2
D [01/Sep/2005:11:47:03 -0500] [Job 10] Inserting option code into "PageSetup" section.
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:03 -0500] [Job 10] %%Page: 2 2
D [01/Sep/2005:11:47:03 -0500] [Job 10] --> Output goes to the FIFO buffer now.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found: %%BeginPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found: %%EndPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] End of page header
D [01/Sep/2005:11:47:03 -0500] [Job 10] Stopping search for page header options
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:03 -0500] [Job 10] =KH*t9oj+sf&q+o--FTS]!81*q;WB)I%dbtlmpVlf4r0/-Ze"D=d7+1ZPe_7NF*W+ACRWE=9B_.a+5u`
D [01/Sep/2005:11:47:03 -0500] [Job 10] --> Output goes directly to the renderer now.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%3]J-\KP+jE\8,:?Q,dg@03rSZ_^N\a#?25Tp\0H+F'WI@-XE7t\Y3luY7Y0?8IY!:4kjSe"?/g`d;U
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%PageTrailer
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%Page: 3 3
D [01/Sep/2005:11:47:03 -0500] [Job 10] pw = 612.0, pl = 792.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageLeft = 0.0, PageRight = 612.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageTop = 792.0, PageBottom = 0.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageWidth = 612.0, PageLength = 792.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%PageBoundingBox: 0 0 612 792
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%BeginPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%EndPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:03 -0500] [Job 10] New page:  3 3
D [01/Sep/2005:11:47:03 -0500] [Job 10] Inserting option code into "PageSetup" section.
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:03 -0500] [Job 10] %%Page: 3 3
D [01/Sep/2005:11:47:03 -0500] [Job 10] --> Output goes to the FIFO buffer now.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found: %%BeginPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found: %%EndPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] End of page header
D [01/Sep/2005:11:47:03 -0500] [Job 10] Stopping search for page header options
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:03 -0500] [Job 10] &;W.U!;q@6,*BtMb'?OV<@cY$Q,;?nZs,,JX&Xbb?F*n@(eb\9!J\[,ZWV+A@kjFtb2oqqkQ<u>c=\q9
D [01/Sep/2005:11:47:03 -0500] [Job 10] --> Output goes directly to the renderer now.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%PageTrailer
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%Page: 4 4
D [01/Sep/2005:11:47:03 -0500] [Job 10] pw = 612.0, pl = 792.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageLeft = 0.0, PageRight = 612.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageTop = 792.0, PageBottom = 0.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] PageWidth = 612.0, PageLength = 792.0
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%PageBoundingBox: 0 0 612 792
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%BeginPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] 0 %%EndPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:03 -0500] [Job 10] New page:  4 4
D [01/Sep/2005:11:47:03 -0500] [Job 10] Inserting option code into "PageSetup" section.
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:03 -0500] [Job 10] %%Page: 4 4
D [01/Sep/2005:11:47:03 -0500] [Job 10] --> Output goes to the FIFO buffer now.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found: %%BeginPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found: %%EndPageSetup
D [01/Sep/2005:11:47:03 -0500] [Job 10] End of page header
D [01/Sep/2005:11:47:03 -0500] [Job 10] Stopping search for page header options
D [01/Sep/2005:11:47:03 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:03 -0500] [Job 10] <(W<od,&Y&+q\I.q4+$b31\G&F<V;2Ptri(jfsX*A2P25LZ;'!gh-d-N5brCR+-"5*"BpJ=9-ui1`;7l
D [01/Sep/2005:11:47:03 -0500] [Job 10] --> Output goes directly to the renderer now.
D [01/Sep/2005:11:47:03 -0500] [Job 10] 
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%PageTrailer
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%Page: 5 5
D [01/Sep/2005:11:47:04 -0500] [Job 10] pw = 612.0, pl = 792.0
D [01/Sep/2005:11:47:04 -0500] [Job 10] PageLeft = 0.0, PageRight = 612.0
D [01/Sep/2005:11:47:04 -0500] [Job 10] PageTop = 792.0, PageBottom = 0.0
D [01/Sep/2005:11:47:04 -0500] [Job 10] PageWidth = 612.0, PageLength = 792.0
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%PageBoundingBox: 0 0 612 792
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%BeginPageSetup
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%EndPageSetup
D [01/Sep/2005:11:47:04 -0500] [Job 10] 
D [01/Sep/2005:11:47:04 -0500] [Job 10] -----------
D [01/Sep/2005:11:47:04 -0500] [Job 10] New page:  5 5
D [01/Sep/2005:11:47:04 -0500] [Job 10] Inserting option code into "PageSetup" section.
D [01/Sep/2005:11:47:04 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:04 -0500] [Job 10] %%Page: 5 5
D [01/Sep/2005:11:47:04 -0500] [Job 10] --> Output goes to the FIFO buffer now.
D [01/Sep/2005:11:47:04 -0500] [Job 10] 
D [01/Sep/2005:11:47:04 -0500] [Job 10] 
D [01/Sep/2005:11:47:04 -0500] [Job 10] Found: %%BeginPageSetup
D [01/Sep/2005:11:47:04 -0500] [Job 10] Found: %%EndPageSetup
D [01/Sep/2005:11:47:04 -0500] [Job 10] End of page header
D [01/Sep/2005:11:47:04 -0500] [Job 10] Stopping search for page header options
D [01/Sep/2005:11:47:04 -0500] [Job 10] Found:
D [01/Sep/2005:11:47:04 -0500] [Job 10] #,<nlWn&a?NsGj(R&jI@'FBGe5nJ]7+;!D5J`kM8nEXmAcfVQbb-YP,Pk!iZM+"2&-tJ3(=92[4=Y(7Z
D [01/Sep/2005:11:47:04 -0500] [Job 10] --> Output goes directly to the renderer now.
D [01/Sep/2005:11:47:04 -0500] [Job 10] 
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%pKTUF.HH&cDop7NbDp"#4>JCHA&IV6Z4c[R(]7`$,dQ\c=E$#Xorb:lKKV+Hf<l_DqmN1_bg9_d]V`
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%PageTrailer
D [01/Sep/2005:11:47:04 -0500] [Job 10] 0 %%Trailer
D [01/Sep/2005:11:47:04 -0500] [Job 10] Saw Trailer!
D [01/Sep/2005:11:47:04 -0500] [Job 10] Saw EOF!
D [01/Sep/2005:11:47:04 -0500] [Job 10] 
D [01/Sep/2005:11:47:04 -0500] [Job 10] Closing renderer
D [01/Sep/2005:11:47:04 -0500] [Job 10] KID4 exited with status 0
D [01/Sep/2005:11:47:04 -0500] [Job 10] KID3 exited with status 1
D [01/Sep/2005:11:47:04 -0500] [Job 10] Renderer exit stat: 1
D [01/Sep/2005:11:47:04 -0500] [Job 10] Renderer process finished
D [01/Sep/2005:11:47:04 -0500] [Job 10] Killing process 7299 (KID3)
D [01/Sep/2005:11:47:04 -0500] [Job 10] Process dying with "Error closing renderer", exit stat: 1
D [01/Sep/2005:11:47:04 -0500] [Job 10] Error closing renderer
E [01/Sep/2005:11:47:07 -0500] PID 7296 stopped with status 1!
D [01/Sep/2005:11:47:07 -0500] UpdateJob: job 10, file 0 is complete.
D [01/Sep/2005:11:47:07 -0500] CancelJob: id = 10
D [01/Sep/2005:11:47:07 -0500] StopJob: id = 10, force = 0
D [01/Sep/2005:11:47:07 -0500] StopJob: printer state is 3


What do I need to do?

---


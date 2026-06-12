---
title: "HP 845c Picky about Printing"
date: 2011-06-03
forum: Hardware
---

### Post by KutWrite on 2011-06-03
**Printer is Not Driven Properly** 
Just switched from Mac to Ubuntu 11.04. It was working fine, but then the subject problem, described in detail below.
I'm pretty handy with following instructions, but don't know enough to do "run as root" type of instruction w/o describing the steps. 
 
System Specifics:
Toshiba A665 S2100x laptop (i7 core)
Ubuntu 11.04 updated yesterday
HPLIP removed, reinstalled & updated
HP **[COLOR=#ff0000]845c[/COLOR]** via USB; connected, works with my Win 7 dual-boot and a separate Powerbook when plugged into it. Plenty of ink.
Seen by HPLIP as an HP 845c
CUPS de- and reinstalled; error stated below seems CUPS related (service not available) but only balks on certain docs. 
 
Problem Specifics:
 
My HP **[COLOR=#ff0000]845c[/COLOR]** printer printed OK, then I noticed graphic files, e.g. maps, printed very, very faintly. I only use the black ink cartridge and this has printed OK before.
Used Printing/Setup under System/Prefs to set it to Grayscale. No improvement.
Now it started only printing text files from gedit.
It won't print these:
RTFs from Libre Office
jpgs or gifs from any image handling pgm.
pdfs from Firefox w/plugin, image viewer or Acrobat
 
I set it back to "normal color" ; no change:
 
More details:
 
When I try to print...
 
HPLIP Device Status box first says:
Started a print job 
(when restarting an existing job still in queue, this has a yellow triangle around a "!")
Then:
Print job is processing (name)
 
Then, with a yellow triangle around the "!":
! Print job has completed (but it never printed)
 
New box with red " - " says:
Print Error
There was a problem processing document xxx.rtf (job xx)
Diagnose OK "
 
When I click "Diagnose" & go through the Wizard:
Little box: HLIP Device status: (printer name) Idle"
 
In troubleshooter box:
"E [31/May/2011:21:01:25 -0700] Failed to update TXT record for HEWLETT-PACKARD DESKJET **[COLOR=#ff0000]845C[/COLOR]** @ Dan-Toshiba: -2"
 
CUPS error: 
 
HP **[COLOR=#ff0000]845c[/COLOR]** USB printer
Ubuntu 11.04
latest drivers and HPLIP
tried plugging and unplugging, deleting & reinstalling printer and HPLIP
Tried running printer direcly via USB w/o HPLIP
 
- - - - - -
 
Error Log Messages:
 
E [31/May/2011:20:50:08 -0700] [Job 58] Job stopped due to filter errors; please consult the error_log file for details.
D [31/May/2011:20:50:08 -0700] [Job 58] The following messages were recorded from 20:50:00 to 20:50:08
D [31/May/2011:20:50:08 -0700] [Job 58] Adding start banner page "none".
D [31/May/2011:20:50:08 -0700] [Job 58] Adding end banner page "none".
D [31/May/2011:20:50:08 -0700] [Job 58] File of type application/vnd.cups-banner queued by "daniel".
D [31/May/2011:20:50:08 -0700] [Job 58] hold_until=0
D [31/May/2011:20:50:08 -0700] [Job 58] Queued on "DESKJET-845C" by "daniel".
D [31/May/2011:20:50:09 -0700] [Job 58] job-sheets=none,none
D [31/May/2011:20:50:09 -0700] [Job 58] argv[0]="DESKJET-845C"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[1]="58"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[2]="daniel"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[3]="Test Page"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[4]="1"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[5]="job-uuid=urn:uuid:fc1d94d1-adba-3475-575b-974b28b963ad job-originating-host-name=localhost time-at-creation=1306900200 time-at-processing=1306900200 AP_D_InputSlot="
D [31/May/2011:20:50:09 -0700] [Job 58] argv[6]="/var/spool/cups/d00058-001"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[8]="HOME=/var/spool/cups/tmp"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[10]="SERVER_ADMIN=root@Dan-Toshiba"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[11]="SOFTWARE=CUPS/1.4.6"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[13]="USER=root"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[14]="CUPS_SERVER=localhost"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[16]="IPP_PORT=631"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[17]="CHARSET=utf-8"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[18]="LANG=en_US.UTF-8"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[19]="PPD=/etc/cups/ppd/DESKJET-845C.ppd"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[20]="RIP_MAX_CACHE=auto"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[22]="DEVICE_URI=hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[23]="PRINTER_INFO=HEWLETT-PACKARD DESKJET **[COLOR=#ff0000]845C[/COLOR]**"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[24]="PRINTER_LOCATION=Dan-Toshiba"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[25]="PRINTER=DESKJET-845C"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[26]="CUPS_FILETYPE=document"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[27]="FINAL_CONTENT_TYPE=printer/DESKJET-845C"
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/bannertops (PID 3322)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/pstopdf (PID 3323)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/pdftopdf (PID 3324)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 3325)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/hpcups (PID 3326)
D [31/May/2011:20:50:09 -0700] [Job 58] Started backend /usr/lib/cups/backend/hp (PID 3327)
D [31/May/2011:20:50:09 -0700] [Job 58] pstopdf 5 args: 58 daniel Test Page 1 job-uuid=urn:uuid:fc1d94d1-adba-3475-575b-974b28b963ad job-originating-host-name=localhost time-at-creation=1306900200 time-at-processing=1306900200 AP_D_InputSlot=
D [31/May/2011:20:50:09 -0700] [Job 58] PPD: /etc/cups/ppd/DESKJET-845C.ppd
D [31/May/2011:20:50:09 -0700] [Job 58] load_banner(filename="/var/spool/cups/d00058-001")
D [31/May/2011:20:50:09 -0700] [Job 58] Page = 612x792; 18,36 to 594,783
D [31/May/2011:20:50:09 -0700] [Job 58] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [31/May/2011:20:50:09 -0700] [Job 58] PNG image: 192x128x8, color_type=2 (RGB)
D [31/May/2011:20:50:09 -0700] [Job 58] Resolution:
D [31/May/2011:20:50:09 -0700] [Job 58] Page size: Letter
D [31/May/2011:20:50:09 -0700] [Job 58] Width: 612, height: 792, absolute margins: 18, 36, 594, 783
D [31/May/2011:20:50:09 -0700] [Job 58] Relative margins: 18, 36, 18, 9
D [31/May/2011:20:50:09 -0700] [Job 58] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [31/May/2011:20:50:09 -0700] [Job 58] PostScript to be injected:
D [31/May/2011:20:50:09 -0700] [Job 58] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/printer -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=- -c .setpdfwrite -f -
D [31/May/2011:20:50:09 -0700] [Job 58] mediaBox = [ 0.000000 0.000000 612.000000 792.000000 ]
D [31/May/2011:20:50:09 -0700] [Job 58] size = Letter
D [31/May/2011:20:50:09 -0700] [Job 58] STATE: +connecting-to-device
D [31/May/2011:20:50:09 -0700] [Job 58] prnt/hpcups/Pcl3Gui.cpp 75: Requested resolution not supported with requested printmodeprnt/hpcups/HPCupsFilter.cpp 420: m_Job initialization failed with error = 25STATE: -connecting-to-device
D [31/May/2011:20:50:09 -0700] [Job 58] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [31/May/2011:20:50:09 -0700] [Job 58] ready to print
D [31/May/2011:20:50:09 -0700] [Job 58] End of messages
D [31/May/2011:20:50:09 -0700] [Job 58] printer-state=3(idle)
D [31/May/2011:20:50:09 -0700] [Job 58] printer-state-message="ready to print"
D [31/May/2011:20:50:09 -0700] [Job 58] printer-state-reasons=none
E [31/May/2011:20:53:36 -0700] Failed to update TXT record for HEWLETT-PACKARD DESKJET **[COLOR=#ff0000]845C[/COLOR]** @ Dan-Toshiba: -2
 
- - - - - -
 
Note: Near the bottom it says: 
Test Page printed = true <------- But this statement is false
 
 
Other info:
 
Diagnostic Output (Advanced)
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest DESKJET-845C (default)>,
'cups_instance': None,
'cups_queue': 'DESKJET-845C',
'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
'cups_printer_dict': {'device-uri': u'hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX',
'printer-info': u'HEWLETT-PACKARD DESKJET **[COLOR=#ff0000]845C[/COLOR]**',
'printer-is-shared': True,
'printer-location': u'Dan-Toshiba',
'printer-make-and-model': u'HP Deskjet **[COLOR=#ff0000]845c[/COLOR]**, hpcups 3.11.5',
'printer-state': 3,
'printer-state-message': u'ready to print',
'printer-state-reasons': [u'none'],
'printer-type': 167948,
'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET-845C'},
'cups_printer_remote': False,
'hplip_output': (['',
'\x1b[01mHP Linux Imaging and Printing System (ver. 3.11.5)\x1b[0m',
'\x1b[01mDevice Information Utility ver. 5.2\x1b[0m',
'',
'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
'This software comes with ABSOLUTELY NO WARRANTY.',
'This is free software, and you are welcome to distribute it',
'under certain conditions. See COPYING file for more details.',
'',
'',
'\x1b[01mhp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX\x1b[0m',
'',
'\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
'\x1b[01m Parameter Value(s) \x1b[0m',
' ---------------------------- ----------------------------------------------------------',
' agent1-ack False ',
' agent1-desc Black cartridge ',
' agent1-dvc 0 ',
' agent1-health 0 ',
' agent1-health-desc Good/OK ',
' agent1-hp-ink False ',
' agent1-id 0 ',
' agent1-kind 3 ',
' agent1-known False ',
' agent1-level 0 ',
' agent1-level-trigger 0 ',
' agent1-sku 15 (C6615DN) ',
' agent1-type 1 ',
' agent1-virgin False ',
' back-end hp ',
" cups-printers ['DESKJET-845C'] ",
' cups-uri hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX ',
' dev-file ',
' device-state 1 ',
' device-uri hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX ',
' deviceid MFG:HEWLETT-PACKARD;MDL:grin:ESKJET ',
' **[COLOR=#ff0000]845C[/COLOR]**;CMD:MLC,PCL,PML;CLASS:razz:RINTER;DESCRIPTION:Hew lett-Pac',
' kard DeskJet ',
' **[COLOR=#ff0000]845C[/COLOR]**;SERN:CN19Q1C0J9SX;VSTATUS:$HB0$AU0,ff,DN,IDLE ,CUT;VP:',
' 0800,FL,B0; ',
' duplexer 0 ',
' error-state 0 ',
' host ',
' in-tray1 0 ',
' in-tray2 0 ',
' is-hp True ',
' media-path 1 ',
' panel 0 ',
' panel-line1 ',
' panel-line2 ',
' photo-tray 0 ',
' port 1 ',
' r 0 ',
' revision 255 ',
' rg 000 ',
' rr 000000 ',
' rs 000000000 ',
' serial CN19Q1C0J9SX ',
' status-code 1000 ',
' status-desc Idle ',
' supply-door 0 ',
' top-door 1 ',
'\x1b[01m',
'Model Parameters (static data):\x1b[0m',
'\x1b[01m Parameter Value(s) \x1b[0m',
' ---------------------------- ----------------------------------------------------------',
' align-type 2 ',
' clean-type 1 ',
' color-cal-type 0 ',
' copy-type 0 ',
' embedded-server-type 0 ',
' fax-type 0 ',
' fw-download False ',
' icon DESKJET_840C.png ',
' io-mfp-mode 6 ',
' io-mode 1 ',
' io-support 2 ',
' job-storage 0 ',
' linefeed-cal-type 0 ',
' model DeskJet_845C ',
' model-ui HP Deskjet **[COLOR=#ff0000]845c[/COLOR]** ',
' model1 HP Deskjet **[COLOR=#ff0000]845c[/COLOR]** Printer ',
' model2 HP Deskjet 845cvr Printer ',
' monitor-type 0 ',
' panel-check-type 0 ',
' pcard-type 0 ',
' plugin 0 ',
' plugin-reason 0 ',
' power-settings 0 ',
' pq-diag-type 0 ',
' r-type 0 ',
' r0-agent1-kind 3 ',
' r0-agent1-sku 15 (C6615DN) ',
' r0-agent1-type 1 ',
' r0-agent2-kind 3 ',
' r0-agent2-sku 17 (C6625AN) ',
' r0-agent2-type 2 ',
' scan-style 0 ',
' scan-type 0 ',
' status-battery-check 0 ',
' status-dynamic-counters 0 ',
' status-type 1 ',
' support-released True ',
' support-subtype 2202411 ',
' support-type 2 ',
' support-ver 0.9.5 ',
" tech-class ['DJ8x5'] ",
" tech-subclass ['Normal'] ",
' tech-type 2 ',
' usb-pid 2308 ',
' usb-vid 1008 ',
' wifi-config 0 ',
'\x1b[01m',
'Status History (most recent first):\x1b[0m',
'\x1b[01m Date/Time Code Status Description User Job ID \x1b[0m',
' -------------------- ----- ---------------------------------------- -------- --------',
' 05/31/11 21:00:37 1000 Idle daniel 0 ',
' 05/31/11 20:58:04 501 Print job has completed daniel 57 ',
' 05/31/11 20:57:56 500 Started a print job daniel 57 ',
' 05/31/11 20:50:08 501 Print job has completed daniel 58 ',
' 05/31/11 20:50:00 500 Started a print job daniel 58 ',
' 05/31/11 20:49:13 1000 Idle daniel 0 ',
' 05/31/11 20:48:51 501 Print job has completed daniel 57 ',
' 05/31/11 20:48:42 500 Started a print job daniel 57 ',
' 05/31/11 20:16:40 1000 Idle daniel 0 ',
' 05/31/11 17:45:07 501 Print job has completed daniel 56 ',
' 05/31/11 17:44:57 500 Started a print job daniel 56 ',
' 05/31/11 17:44:57 501 Print job has completed daniel 55 ',
' 05/31/11 17:43:46 500 Started a print job daniel 55 ',
' 05/31/11 17:43:20 501 Print job has completed daniel 54 ',
' 05/31/11 17:43:12 500 Started a print job daniel 54 ',
' 05/31/11 17:41:31 1000 Idle daniel 0 ',
' 05/31/11 17:41:00 501 Print job has completed daniel 53 ',
' 05/31/11 17:40:51 500 Started a print job daniel 53 ',
' 05/31/11 17:38:00 501 Print job has completed daniel 52 ',
' 05/31/11 17:37:57 5021 Device is busy daniel 0 ',
' 05/31/11 17:37:50 500 Started a print job daniel 52 ',
' 05/31/11 17:37:50 1000 Idle daniel 0 ',
' 05/31/11 17:35:22 501 Print job has completed daniel 50 ',
' 05/31/11 17:35:13 500 Started a print job daniel 50 ',
' 05/31/11 17:33:20 501 Print job has completed daniel 51 ',
' 05/31/11 17:33:02 500 Started a print job daniel 51 ',
' 05/31/11 17:31:27 501 Print job has completed daniel 50 ',
' 05/31/11 17:31:17 500 Started a print job daniel 50 ',
' 05/31/11 17:30:30 1000 Idle daniel 0 ',
' 05/31/11 17:30:02 501 Print job has completed daniel 49 ',
' 05/31/11 17:29:53 500 Started a print job daniel 49 ',
' 05/31/11 17:29:15 1000 Idle daniel 0 ',
' 05/31/11 17:29:04 501 Print job has completed daniel 49 ',
' 05/31/11 17:28:54 500 Started a print job daniel 49 ',
' 05/31/11 17:28:45 501 Print job has completed daniel 49 ',
' 05/31/11 17:28:35 500 Started a print job daniel 49 ',
' 05/31/11 17:24:32 501 Print job has completed daniel 48 ',
' 05/31/11 17:23:43 500 Started a print job daniel 48 ',
' 05/31/11 17:21:00 501 Print job has completed daniel 47 ',
' 05/31/11 17:20:14 500 Started a print job daniel 47 ',
'',
'',
'Done.',
''],
['\x1b[35;01mwarning: No display found.\x1b[0m',
'\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
''],
0),
'is_cups_class': False,
'local_cups_queue_attributes': {'auth-info-required': u'none',
'charset-configured': u'utf-8',
'charset-supported': [u'us-ascii', u'utf-8'],
'color-supported': True,
'compression-supported': [u'none', u'gzip'],
'copies-default': 1,
'copies-supported': (1, 9999),
'cups-version': u'1.4.6',
'device-uri': u'hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX',
'document-format-default': u'application/octet-stream',
'document-format-supported': [u'application/octet-stream',
u'application/openofficeps',
u'application/pdf',
u'application/postscript',
u'application/vnd.cups-banner',
u'application/vnd.cups-pdf',
u'application/vnd.cups-postscript',
u'application/vnd.cups-raster',
u'application/vnd.cups-raw',
u'application/vnd.hp-hpgl',
u'application/x-cshell',
u'application/x-csource',
u'application/x-perl',
u'application/x-shell',
u'image/gif',
u'image/jpeg',
u'image/png',
u'image/tiff',
u'image/x-bitmap',
u'image/x-photocd',
u'image/x-portable-anymap',
u'image/x-portable-bitmap',
u'image/x-portable-graymap',
u'image/x-portable-pixmap',
u'image/x-sgi-rgb',
u'image/x-sun-raster',
u'image/x-xbitmap',
u'image/x-xpixmap',
u'image/x-xwindowdump',
u'text/css',
u'text/html',
u'text/plain'],
'finishings-default': 3,
'finishings-supported': [3],
'generated-natural-language-supported': [u'en-us'],
'ipp-versions-supported': [u'1.0',
u'1.1',
u'2.0',
u'2.1'],
'ippget-event-life': 15,
'job-creation-attributes-supported': [u'copies',
u'finishings',
u'ipp-attribute-fidelity',
u'job-hold-until',
u'job-name',
u'job-priority',
u'job-sheets',
u'media',
u'media-col',
u'multiple-document-handling',
u'number-up',
u'output-bin',
u'output-mode',
u'orientation-requested',
u'page-ranges',
u'print-quality',
u'printer-resolution',
u'sides'],
'job-hold-until-default': u'no-hold',
'job-hold-until-supported': [u'no-hold',
u'indefinite',
u'day-time',
u'evening',
u'night',
u'second-shift',
u'third-shift',
u'weekend'],
'job-k-limit': 0,
'job-page-limit': 0,
'job-priority-default': 50,
'job-priority-supported': [100],
'job-quota-period': 0,
'job-settable-attributes-supported': [u'copies',
u'finishings',
u'job-hold-until',
u'job-name',
u'job-priority',
u'media',
u'media-col',
u'multiple-document-handling',
u'number-up',
u'output-bin',
u'output-mode',
u'orientation-requested',
u'page-ranges',
u'print-quality',
u'printer-resolution',
u'sides'],
'job-sheets-default': (u'none', u'none'),
'job-sheets-supported': [u'none',
u'classified',
u'confidential',
u'secret',
u'standard',
u'topsecret',
u'unclassified'],
'marker-change-time': 0,
'media-bottom-margin-supported': [1270],
'media-col-supported': [u'media-bottom-margin',
u'media-left-margin',
u'media-right-margin',
u'media-size',
u'media-source',
u'media-top-margin',
u'media-type'],
'media-default': u'na_letter_8.5x11in',
'media-left-margin-supported': [635, 317],
'media-right-margin-supported': [635, 317],
'media-source-supported': [u'auto',
u'photo',
u'top',
u'bottom',
u'envelope',
u'large-capacity',
u'manual',
u'alternate'],
'media-supported': [u'oe_card3x5_3x5in',
u'om_hagaki_100.18x148.16mm',
u'oe_photo4x6_4x6in',
u'iso_a6_105x148mm',
u'oe_photo5x7_5x7in',
u'oe_card5x8_5x8in',
u'om_oufuku_200.02x148.16mm',
u'iso_a5_148x210mm',
u'jis_b5_182x257mm',
u'om_jb5_182.11x257.04mm',
u'na_executive_7.25x10.5in',
u'oe_16k_7.75x10.75in',
u'na_letter_8.5x11in',
u'iso_a4_210x297mm',
u'na_legal_8.5x14in',
u'om_env-a2_110.99x146.05mm',
u'iso_c6_114x162mm',
u'jpn_chou4_90x205mm',
u'na_monarch_3.875x7.5in',
u'iso_dl_110x220mm',
u'na_number-10_4.125x9.5in',
u'jpn_chou3_120x235mm',
u'iso_c5_162x229mm',
u'om_env-b5_176.03x250.11mm',
u'custom_min_1x4in',
u'custom_max_8.5x14in'],
'media-top-margin-supported': [317],
'media-type-supported': [u'stationery',
u'photographic-glossy'],
'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
u'separate-documents-collated-copies'],
'multiple-document-jobs-supported': True,
'multiple-operation-time-out': 300,
'natural-language-configured': u'en-us',
'notify-attributes-supported': [u'printer-state-change-time',
u'notify-lease-expiration-time',
u'notify-subscriber-user-name'],
'notify-events-default': [u'job-completed'],
'notify-events-supported': [u'job-completed',
u'job-config-changed',
u'job-created',
u'job-progress',
u'job-state-changed',
u'job-stopped',
u'printer-added',
u'printer-changed',
u'printer-config-changed',
u'printer-deleted',
u'printer-finishings-changed',
u'printer-media-changed',
u'printer-modified',
u'printer-restarted',
u'printer-shutdown',
u'printer-state-changed',
u'printer-stopped',
u'server-audit',
u'server-restarted',
u'server-started',
u'server-stopped'],
'notify-lease-duration-default': 86400,
'notify-lease-duration-supported': (0,
2147483647),
'notify-max-events-supported': [100],
'notify-pull-method-supported': [u'ippget'],
'notify-schemes-supported': [u'dbus',
u'mailto',
u'rss'],
'number-up-default': 1,
'number-up-supported': [1, 2, 4, 6, 9, 16],
'operations-supported': [2,
4,
5,
6,
8,
9,
10,
11,
12,
13,
16,
17,
18,
19,
20,
21,
22,
23,
24,
25,
26,
27,
28,
34,
35,
37,
38,
16385,
16386,
16387,
16388,
16389,
16390,
16391,
16392,
16393,
16394,
16395,
16396,
16397,
16398,
16399,
16423],
'orientation-requested-default': None,
'orientation-requested-supported': [3,
4,
5,
6],
'output-bin-default': u'face-down',
'output-bin-supported': [u'face-down'],
'output-mode-default': u'color',
'output-mode-supported': [u'monochrome',
u'color'],
'page-ranges-supported': True,
'pages-per-minute': 1,
'pages-per-minute-color': 1,
'pdl-override-supported': [u'attempted'],
'port-monitor': u'none',
'port-monitor-supported': [u'none'],
'print-quality-default': 4,
'print-quality-supported': [4],
'printer-commands': u'none',
'printer-current-time': '(IPP_TAG_DATE)',
'printer-error-policy': u'retry-job',
'printer-error-policy-supported': [u'abort-job',
u'retry-current-job',
u'retry-job',
u'stop-printer'],
'printer-icons': u'http://localhost:631/icons/DESKJET-845C.png',
'printer-info': u'HEWLETT-PACKARD DESKJET **[COLOR=#ff0000]845C[/COLOR]**',
'printer-is-accepting-jobs': True,
'printer-is-shared': True,
'printer-location': u'Dan-Toshiba',
'printer-make-and-model': u'HP Deskjet **[COLOR=#ff0000]845c[/COLOR]**, hpcups 3.11.5',
'printer-more-info': u'http://localhost:631/printers/DESKJET-845C',
'printer-name': u'DESKJET-845C',
'printer-op-policy': u'default',
'printer-op-policy-supported': [u'authenticated',
u'default'],
'printer-resolution-default': '(unknown IPP tag)',
'printer-resolution-supported': '(unknown IPP tag)',
'printer-settable-attributes-supported': [u'printer-info',
u'printer-location'],
'printer-state': 3,
'printer-state-change-time': 1306900684,
'printer-state-message': u'ready to print',
'printer-state-reasons': [u'none'],
'printer-type': 167948,
'printer-up-time': 1306900837,
'printer-uri-supported': [u'ipp://localhost:631/printers/DESKJET-845C'],
'queued-job-count': 2,
'server-is-sharing-printers': True,
'sides-default': u'one-sided',
'sides-supported': [u'one-sided'],
'uri-authentication-supported': [u'requesting-user-name'],
'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'InputSlot': u'Auto',
u'MediaType': u'Plain',
u'OutputMode': u'NormalGray',
u'PageRegion': u'Letter',
u'PageSize': u'Letter'}},
'cups_printer_ppd_valid': True,
'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
'device-id': u'MFG:Hewlett-Packard;MDL:grin:eskJet **[COLOR=#ff0000]845C[/COLOR]**;CLS:razz:RINTER;DES:grin:eskJet **[COLOR=#ff0000]845C[/COLOR]**;SN:CN19Q1C0J9SX;',
'device-info': u'HP DeskJet **[COLOR=#ff0000]845C[/COLOR]** USB CN19Q1C0J9SX HPLIP',
'device-location': u'',
'device-make-and-model': u'HP DeskJet **[COLOR=#ff0000]845C[/COLOR]**'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseAddress': '@LOCAL',
'BrowseLocalProtocols': 'CUPS dnssd',
'BrowseOrder': 'allow,deny',
'BrowseRemoteProtocols': '',
'Browsing': 'On',
'DefaultAuthType': 'Basic',
'LogLevel': 'warn',
'MaxLogSize': '0',
'SystemGroup': 'lpadmin',
'_debug_logging': '0',
'_remote_admin': '0',
'_remote_any': '1',
'_remote_printers': '0',
'_share_printers': '1',
'_user_cancel_any': '0'},
'error_log_checkpoint': 222012L,
'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_job_status': [(True,
57,
'DESKJET-845C',
'MiscInfo',
'Stopped',
{'PageSize': u'Letter',
'attributes-charset': u'utf-8',
'attributes-natural-language': u'en-us',
'document-count': 1,
'document-format': u'application/postscript',
'job-hold-until': u'no-hold',
'job-id': 57,
'job-k-octets': 262,
'job-media-progress': 0,
'job-media-sheets-completed': 0,
'job-more-info': u'ipp://localhost:631/jobs/57',
'job-name': u'MiscInfo',
'job-originating-host-name': u'localhost',
'job-originating-user-name': u'daniel',
'job-preserved': True,
'job-printer-state-message': u'/usr/lib/cups/filter/hpcups failed',
'job-printer-state-reasons': [u'none'],
'job-printer-up-time': 1306900885,
'job-printer-uri': u'ipp://Dan-Toshiba:631/printers/DESKJET-845C',
'job-priority': 50,
'job-sheets': [u'none', u'none'],
'job-state': 6,
'job-state-reasons': u'job-stopped',
'job-uri': u'ipp://localhost:631/jobs/57',
'job-uuid': u'urn:uuid:87ee4a99-55a7-3ddd-5744-de794cfad96f',
'printer-uri': u'ipp://localhost:631/printers/DESKJET-845C',
'time-at-completed': None,
'time-at-creation': 1306900122,
'time-at-processing': 1306900676}),
(False,
58,
'DESKJET-845C',
'Test Page',
'Stopped',
None)],
'test_page_successful': True}
Page 9 (Error log fetch):
{'error_log': ['E [31/May/2011:21:01:25 -0700] Failed to update TXT record for HEWLETT-PACKARD DESKJET **[COLOR=#ff0000]845C[/COLOR]** @ Dan-Toshiba: -2'],
'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'job_page_size': u'Letter',
'printer_page_size': u'Letter',
'system_locale_lang': None,
'user_locale_ctype': 'en_US',
'user_locale_messages': 'en_US'}
 
- - - - -
 
I've tried removing and reinstalling the printer, hplip, hjif (?) via the Synaptic option.
No change in the effect, but now I have a little blue HP logo on the top panel. Wowie!
 
Can you help me?

---

### Post by KutWrite on 2011-06-04
Anyone?

Anyone?

Buehler?

---

### Post by KutWrite on 2011-06-05
Update:  It will print emails directly from Evolution.  Still won't print PDFs.

Maybe somehow bypassing HPLIP makes it work?

Anyone?

---

### Post by KutWrite on 2011-06-06
Might've fixed it:

My laptop is dual-boot; booted to Win7 and the printer worked, after I told it it could download the right driver.  So...

1. Booted to Ubuntu

2. Selected System/Admin/Printing

3. Deleted "New Group" and HP 845c there which used HPLIP

4. Created new HP 845c printer which used USB instead of HPLIP
    (note: Ended up doing this 4x, since it doesn't show the created printer - thought I'd messed up
      so when they did show on re-selecting "Printing," I deleted the extra ones)

5. Printed test page - worked fine!  Printed a PDF and a web page - fine!

6. Changed printer attributes to "normal grey scale" due to not using color inks - Ehhhhh! Stopped working
    Printer works on either "normal color" (with bad rendition of colors)
    or on "Draft Grey Scale" which is actually just fine except for photos.

Summary: A combination of eschewing HPLIP for USB and not selecting "Normal Grey Scale"
                 made it work.

So, hopefully this will be of more help than the "usual nerds" who ignored my plight.

---

### Post by Elfy on 2011-06-06
duplicate closed.

---


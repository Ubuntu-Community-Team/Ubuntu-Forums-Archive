---
title: "printer is not working OL-T2300"
date: 2013-10-07
forum: Hardware
---

### Post by hontein on 2013-10-07
Sorry for the english , I use translator. I have a Chinese printer OL-T2300 (POS / ESC). It is made on the basis of Epson TM88. The seller gave me a printer driver for linux, but they do not fit. I can not understand why. Not suitable driver or am I wrong to install them in the system?
My knowledge of linux is not enough to solve the problem. The test page is printed , but not right. If you print any document into cups reports an error . I understand the error in text-to- POS / ESC command. What do I do?


Technical data:
The printer connects via USB


Linux oleg-EB1007 3.8.0- 19 -generic # 29 -Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU / Linux


Package: cups
Status: install ok installed
Architecture: amd64
Version: 1.6.2-1ubuntu5




Package: cups-filters
Status: install ok installed
Architecture: amd64
Version: 1.0.34-0ubuntu1.1

log file cups
```
E [03/Oct/2013:15:37:18 +0400] [Job 34] Job stopped due to filter errors; please consult the error_log file for details.
D [03/Oct/2013:15:37:18 +0400] [Job 34] The following messages were recorded from 15:37:17 to 15:37:18
D [03/Oct/2013:15:37:18 +0400] [Job 34] Adding start banner page "none".
D [03/Oct/2013:15:37:18 +0400] [Job 34] Adding end banner page "none".
D [03/Oct/2013:15:37:18 +0400] [Job 34] File of type application/pdf queued by "oleg".
D [03/Oct/2013:15:37:18 +0400] [Job 34] hold_until=0
D [03/Oct/2013:15:37:18 +0400] [Job 34] Queued on "121" by "oleg".
D [03/Oct/2013:15:37:18 +0400] [Job 34] time-at-processing=1380800237
D [03/Oct/2013:15:37:18 +0400] [Job 34] job-sheets=none,none
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[0]="121"
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[1]="34"
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[2]="oleg"
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[3]="&#1041;&#1077;&#1079;&#1099;&#1084;&#1103;&#1085;&#1085;&#1099;&#1081; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090; 2"
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[4]="1"
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[5]="TmtDrawer1=Off TmtDrawer2=Off TmtBuzzerControl=Off PageSize=Custom.A4 number-up=1 TmtPaperSource=DocFeedCut TmtBuzzerRepeat=1 TmtPaperReduction=Bottom TmtSpeed=Auto job-uuid=urn:uuid:0ed8c3f8-394d-397b-5593-9dc568382201 job-originating-host-name=localhost time-at-creation=1380800237 time-at-processing=1380800237"
D [03/Oct/2013:15:37:18 +0400] [Job 34] argv[6]="/var/spool/cups/d00034-001"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[10]="SERVER_ADMIN=root@oleg-EB1007"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[11]="SOFTWARE=CUPS/1.6.2"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[13]="USER=root"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[14]="CUPS_MAX_MESSAGE=2047"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[17]="IPP_PORT=631"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[18]="CHARSET=utf-8"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[19]="LANG=ru_RU.UTF-8"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[20]="PPD=/etc/cups/ppd/121.ppd"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[21]="RIP_MAX_CACHE=128m"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[22]="CONTENT_TYPE=application/pdf"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[23]="DEVICE_URI=usb://Unknown/Printer"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[24]="PRINTER_INFO="
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[25]="PRINTER_LOCATION="
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[26]="PRINTER=121"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[27]="PRINTER_STATE_REASONS=none"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[28]="CUPS_FILETYPE=document"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[29]="FINAL_CONTENT_TYPE=printer/121"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[30]="AUTH_I****"
D [03/Oct/2013:15:37:18 +0400] [Job 34] Started filter /usr/lib/cups/filter/pdftopdf (PID 13320)
D [03/Oct/2013:15:37:18 +0400] [Job 34] Started filter /usr/lib/cups/filter/gstoraster (PID 13321)
D [03/Oct/2013:15:37:18 +0400] [Job 34] Started filter /usr/lib/cups/filter/rastertotmt (PID 13322)
D [03/Oct/2013:15:37:18 +0400] [Job 34] Started backend /usr/lib/cups/backend/usb (PID 13323)
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups] Invalid parameter. (PageSize=Custom)
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups] commandOutputRaster = 2
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]             modelNo = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]          resolution = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]          pageHeight = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]           pageWidth = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]     pageBitPerPixel = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]    pageBytesPerLine = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]      paperReduction = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]             drawer1 = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]         drawer1Time = ON:0 OFF:0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]             drawer2 = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]         drawer2Time = ON:0 OFF:0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]         paperSource = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]               speed = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]          speedValue = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]              rotate = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]               pitch = 0.000000
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]       feedManualCut = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups]           bandLines = 0
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups] Failed get parameters.
D [03/Oct/2013:15:37:18 +0400] [Job 34] [tmt-cups] Failed initializes process.
D [03/Oct/2013:15:37:18 +0400] [Job 34] PID 13322 (/usr/lib/cups/filter/rastertotmt) stopped with status 255 (Unknown error 155)
D [03/Oct/2013:15:37:18 +0400] [Job 34] Hint: Try setting the LogLevel to "debug" to find out more.
D [03/Oct/2013:15:37:18 +0400] [Job 34] Printing on printer with URI: usb://Unknown/Printer
D [03/Oct/2013:15:37:18 +0400] [Job 34] PPD uses qualifier 'Gray..180x180dpi'
D [03/Oct/2013:15:37:18 +0400] [Job 34] Calling FindDeviceById(121)
D [03/Oct/2013:15:37:18 +0400] [Job 34] Failed to send: org.freedesktop.ColorManager.NotFound:device id '121' does not exists
D [03/Oct/2013:15:37:18 +0400] [Job 34] Failed to get profile filename!
D [03/Oct/2013:15:37:18 +0400] [Job 34] no profiles specified in PPD
D [03/Oct/2013:15:37:18 +0400] [Job 34] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -r180x180 -dDEVICEWIDTHPOINTS=0 -dDEVICEHEIGHTPOINTS=0 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsRowCount=24 -scupsPageSizeName=Custom -I/usr/share/cups/fonts -c -f -_
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[10]="SERVER_ADMIN=root@oleg-EB1007"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[11]="SOFTWARE=CUPS/1.6.2"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[12]="USER=root"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[13]="CUPS_MAX_MESSAGE=2047"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[16]="IPP_PORT=631"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[17]="CHARSET=utf-8"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[18]="LANG=ru_RU.UTF-8"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[19]="PPD=/etc/cups/ppd/121.ppd"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[20]="RIP_MAX_CACHE=128m"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[21]="CONTENT_TYPE=application/pdf"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[22]="DEVICE_URI=usb://Unknown/Printer"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[23]="PRINTER_INFO="
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[24]="PRINTER_LOCATION="
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[25]="PRINTER=121"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[26]="PRINTER_STATE_REASONS=none"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[27]="CUPS_FILETYPE=document"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[28]="FINAL_CONTENT_TYPE=printer/121"
D [03/Oct/2013:15:37:18 +0400] [Job 34] envp[29]="AUTH_INFO_REQUIRED=none"
D [03/Oct/2013:15:37:18 +0400] [Job 34] PID 13320 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [03/Oct/2013:15:37:18 +0400] [Job 34] libusb_get_device_list=9
D [03/Oct/2013:15:37:18 +0400] [Job 34] STATE: +connecting-to-device
D [03/Oct/2013:15:37:18 +0400] [Job 34] STATE: -connecting-to-device
D [03/Oct/2013:15:37:18 +0400] [Job 34] Printer found with device ID:  Device URI: usb://Unknown/Printer
D [03/Oct/2013:15:37:18 +0400] [Job 34] Device protocol: 2
D [03/Oct/2013:15:37:18 +0400] [Job 34] Printer reports bi-di support but in reality works only uni-directionally
D [03/Oct/2013:15:37:18 +0400] [Job 34] Uni-directional USB communication only!
D [03/Oct/2013:15:37:18 +0400] [Job 34] Printer does not like usblp kernel module to be re-attached after job
D [03/Oct/2013:15:37:18 +0400] [Job 34] Uni-directional device/mode, back channel deactivated.
D [03/Oct/2013:15:37:18 +0400] [Job 34] Sending data to printer.
D [03/Oct/2013:15:37:18 +0400] [Job 34] Sent 0 bytes...
D [03/Oct/2013:15:37:18 +0400] [Job 34] Start rendering...
D [03/Oct/2013:15:37:18 +0400] [Job 34] Processing page 1...
D [03/Oct/2013:15:37:18 +0400] [Job 34] PID 13323 (/usr/lib/cups/backend/usb) exited with no errors.
D [03/Oct/2013:15:37:18 +0400] [Job 34] Resetting printer.
D [03/Oct/2013:15:37:18 +0400] [Job 34] Unrecoverable error: rangecheck in setpagedevice
D [03/Oct/2013:15:37:18 +0400] [Job 34] Operand stack:
D [03/Oct/2013:15:37:18 +0400] [Job 34] true  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  true  --nostringval--  .LockSafetyParams  true  %MediaSource  0  %MediaDestination  0  LeadingEdge  0  --nostringval--  --nostringval--  --nostringval--  0  --nostringval--  false  --nostringval--
D [03/Oct/2013:15:37:18 +0400] [Job 34] Rendering completed
D [03/Oct/2013:15:37:18 +0400] [Job 34] PID 13321 (/usr/lib/cups/filter/gstoraster) exited with no errors.
D [03/Oct/2013:15:37:18 +0400] [Job 34] End of messages
D [03/Oct/2013:15:37:18 +0400] [Job 34] printer-state=3(idle)
D [03/Oct/2013:15:37:18 +0400] [Job 34] printer-state-message="Rendering completed"
D [03/Oct/2013:15:37:18 +0400] [Job 34] printer-state-reasons=none



```
in the attached files incorrect test page 
.[ATTACH=CONFIG]246801[/ATTACH]

---


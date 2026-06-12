---
title: "Canon MF3010 Ubuntu 12.10 printing problems"
date: 2013-03-19
forum: Hardware
---

### Post by eboats on 2013-03-19
I recently got a Canon MF3010 laser printer and am unable to print after installing the drivers.  I'm on Ubuntu 12.10, 64bit.  

I followed the below post but am not able to print a test page.  

[http://ubuntuforums.org/showthread.php?t=2089269](http://ubuntuforums.org/showthread.php?t=2089269)

After trying to print a test page, the Printer State in the Printer dialog says "Idle - Sending data to printer."   Any idea?

---

### Post by pdc on 2013-03-21
so the MF3010 uses the ubiquituous Canon UFR driver; [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz
[/COLOR]
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

if you download this 2.6 version of the UFR driver from Canon Asia....it is new...........

........for all the witterings about Canon not supporting linux...the new 2.6 version of the UFR driver has 64bit deb packages! Well done Canon!

so the commands would be: after you open a terminal; (copy and paste each command)

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_UFRII_PrinterDriver_V260_uk_EN[/COLOR]

> [COLOR="#FF0000"]cd 64-bit_Driver[/COLOR]

> [COLOR="#FF0000"]cd Debian[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.60-1_amd64.deb[/COLOR]

and then 

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-ufr2-uk_2.60-1_amd64.deb[/COLOR]

...........that ............should have the driver installed and you should be all go ....

if you click on this 

[http://localhost:631/printers/](http://localhost:631/printers/)

it should show your printer;

if not, 

[http://localhost:631/admin](http://localhost:631/admin) should allow to find and add yours......

...in the past one needed symbolic links.......if we see the new 2.6 driver with its dedicated 64bit deb packages work ok............it should ...............Canon should have no shortage of printers to test it on!!

---

### Post by eboats on 2013-04-14
Thanks for the response!  However, after following your instruction, I'm still not able to print from my Dell Inspiron 3520 64bit. I set the LogLevel to debug in the Cups error log and have included its output below after trying to print a doc.  The Printer State shows as Idle when I try to print.  When I go to the Cups Admin Jobs interface at [http://localhost:631/jobs?which_jobs=all](http://localhost:631/jobs?which_jobs=all) , it shows that the Job completed but nothing gets printed.  Any idea?


I [14/Apr/2013:11:43:30 -0700] [Job 15] Adding start banner page "none".
D [14/Apr/2013:11:43:30 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdMarkDirty(----J-)
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [14/Apr/2013:11:43:30 -0700] [Job 15] Adding end banner page "none".
I [14/Apr/2013:11:43:30 -0700] [Job 15] File of type application/pdf queued by "mitch".
D [14/Apr/2013:11:43:30 -0700] [Job 15] hold_until=0
I [14/Apr/2013:11:43:30 -0700] [Job 15] Queued on "Canon_MF3010" by "mitch".
D [14/Apr/2013:11:43:30 -0700] cupsdMarkDirty(----J-)
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:30 -0700] [Job 15] job-sheets=none,none
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[0]="Canon_MF3010"
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[1]="15"
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[2]="mitch"
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[3]="Xerox DocuPrint C525A printer"
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[4]="1"
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[5]="noCNDraftMode BindEdge=Left OutputBin=Auto number-up=1 PageSize=Letter InputSlot=Auto noCNOutputAdjustment MediaType=PlainPaper CNHalftone=Gradation CNSpecialPrintMode=Mode1 noCNSpecialPrintAdjustment job-uuid=urn:uuid:605ec659-b101-37af-4842-8be26c947dfc job-originating-host-name=localhost time-at-creation=1365965010 time-at-processing=1365965010"
D [14/Apr/2013:11:43:30 -0700] [Job 15] argv[6]="/var/spool/cups/d00015-001"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[8]="HOME=/var/spool/cups/tmp"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[10]="SERVER_ADMIN=root@mitch-Inspiron-3520"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[11]="SOFTWARE=CUPS/1.5.0"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[13]="USER=root"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[16]="IPP_PORT=631"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[17]="CHARSET=utf-8"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[18]="LANG=en_US.UTF-8"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[19]="PPD=/etc/cups/ppd/Canon_MF3010.ppd"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[20]="RIP_MAX_CACHE=128m"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[21]="CONTENT_TYPE=application/pdf"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[22]="DEVICE_URI=usb://Canon/MF3010?serial=1129Q0062902&interface=1"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[23]="PRINTER_INFO=Canon MF3010"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[24]="PRINTER_LOCATION="
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[25]="PRINTER=Canon_MF3010"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[26]="PRINTER_STATE_REASONS=none"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[27]="CUPS_FILETYPE=document"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[28]="FINAL_CONTENT_TYPE=printer/Canon_MF3010"
D [14/Apr/2013:11:43:30 -0700] [Job 15] envp[29]="AUTH_I****"
I [14/Apr/2013:11:43:30 -0700] [Job 15] Started filter /usr/lib/cups/filter/pdftopdf (PID 2145)
I [14/Apr/2013:11:43:30 -0700] [Job 15] Started filter /usr/lib/cups/filter/cpdftocps (PID 2146)
I [14/Apr/2013:11:43:30 -0700] [Job 15] Started filter /usr/lib/cups/filter/pstoufr2cpca (PID 2147)
I [14/Apr/2013:11:43:30 -0700] [Job 15] Started backend /usr/lib/cups/backend/usb (PID 2148)
D [14/Apr/2013:11:43:30 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:30 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/Canon_MF3010) from localhost
D [14/Apr/2013:11:43:30 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:30 -0700] [Notifier] JobCreated
D [14/Apr/2013:11:43:30 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:30 -0700] [Notifier] PrinterStateChanged
D [14/Apr/2013:11:43:30 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:30 -0700] [Notifier] JobState
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdAcceptClient: 32 from localhost (Domain)
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 32 POST / HTTP/1.1
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 32 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:30 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:30 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:30 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:30 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:30 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:30 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdAcceptClient: 33 from localhost (Domain)
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 33 POST / HTTP/1.1
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:30 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 33 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:30 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:30 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:30 -0700] [Job 15] pdftops argv[5] = 15 mitch Xerox DocuPrint C525A printer 1 noCNDraftMode BindEdge=Left OutputBin=Auto number-up=1 PageSize=Letter InputSlot=Auto noCNOutputAdjustment MediaType=PlainPaper CNHalftone=Gradation CNSpecialPrintMode=Mode1 noCNSpecialPrintAdjustment job-uuid=urn:uuid:605ec659-b101-37af-4842-8be26c947dfc job-originating-host-name=localhost time-at-creation=1365965010 time-at-processing=1365965010
D [14/Apr/2013:11:43:30 -0700] [Job 15] PPD: /etc/cups/ppd/Canon_MF3010.ppd
D [14/Apr/2013:11:43:30 -0700] [Job 15] /usr/bin/pdftops supports '-origpagesizes': yes
D [14/Apr/2013:11:43:30 -0700] [Job 15] print_device
D [14/Apr/2013:11:43:30 -0700] [Job 15] pstoufr2cpca start.
D [14/Apr/2013:11:43:30 -0700] [Job 15] usb_find_busses=2
D [14/Apr/2013:11:43:30 -0700] cupsdReadClient: 30 WAITING Closing on EOF
D [14/Apr/2013:11:43:30 -0700] cupsdCloseClient: 30
D [14/Apr/2013:11:43:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:30 -0700] [Job 15] PostScript Level: 3
D [14/Apr/2013:11:43:31 -0700] [Job 15] Duplex: no
D [14/Apr/2013:11:43:31 -0700] [Job 15] Resolution: 600
D [14/Apr/2013:11:43:31 -0700] [Job 15] Page size: Letter
D [14/Apr/2013:11:43:31 -0700] [Job 15] Width: 612, height: 792, absolute margins: 14.173, 14.173, 597.827, 777.827
D [14/Apr/2013:11:43:31 -0700] [Job 15] Relative margins: 14.173, 14.173, 14.173, 14.173
D [14/Apr/2013:11:43:31 -0700] [Job 15] PPD options: -level3 -origpagesizes
D [14/Apr/2013:11:43:31 -0700] [Job 15] PostScript to be injected: 
D [14/Apr/2013:11:43:31 -0700] PID 2145 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [14/Apr/2013:11:43:31 -0700] [Job 15] usb_find_devices=7
D [14/Apr/2013:11:43:31 -0700] [Job 15] STATE: +connecting-to-device
D [14/Apr/2013:11:43:31 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] [Job 15] STATE: -connecting-to-device
D [14/Apr/2013:11:43:31 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:31 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:31 -0700] [Notifier] PrinterStateChanged
D [14/Apr/2013:11:43:31 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:31 -0700] [Notifier] PrinterStateChanged
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] [Job 15] Device copies: 1; device collate: 
D [14/Apr/2013:11:43:31 -0700] [Job 15] Running /usr/bin/pdftops  -level3 -origpagesizes /tmp/pdftops.AzScT7 -
D [14/Apr/2013:11:43:31 -0700] [Job 15] Running pstops '15' 'mitch' 'Xerox DocuPrint C525A printer' '1' ' noCNDraftMode BindEdge=Left OutputBin=Auto PageSize=Letter InputSlot=Auto noCNOutputAdjustment MediaType=PlainPaper CNHalftone=Gradation CNSpecialPrintMode=Mode1 noCNSpecialPrintAdjustment job-uuid=urn:uuid:605ec659-b101-37af-4842-8be26c947dfc job-originating-host-name=localhost time-at-creation=1365965010 time-at-processing=1365965010'
D [14/Apr/2013:11:43:31 -0700] [Job 15] Page = 612x792; 14,14 to 598,778
D [14/Apr/2013:11:43:31 -0700] [Job 15] slow_collate=0, slow_duplex=0, slow_order=0
D [14/Apr/2013:11:43:31 -0700] [Job 15] Before copy_comments - %!PS-Adobe-3.0
D [14/Apr/2013:11:43:31 -0700] [Job 15] %!PS-Adobe-3.0
D [14/Apr/2013:11:43:31 -0700] [Job 15] %%LanguageLevel: 3
D [14/Apr/2013:11:43:31 -0700] [Job 15] %%DocumentSuppliedResources: (atend)
D [14/Apr/2013:11:43:31 -0700] [Job 15] %%DocumentMedia: plain 612 792 0 () ()
D [14/Apr/2013:11:43:31 -0700] [Job 15] %%BoundingBox: 0 0 612 792
D [14/Apr/2013:11:43:31 -0700] [Job 15] %%Pages: 1
D [14/Apr/2013:11:43:31 -0700] [Job 15] %%EndComments
D [14/Apr/2013:11:43:31 -0700] [Job 15] Before copy_prolog - %%BeginDefaults
D [14/Apr/2013:11:43:31 -0700] [Job 15] Before copy_setup - %%BeginSetup
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 30 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 30 1.1 Get-Notifications 1
D [14/Apr/2013:11:43:31 -0700] Get-Notifications /
D [14/Apr/2013:11:43:31 -0700] cupsdIsAuthorized: requesting-user-name="mitch"
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 34 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 35 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 34 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 34 1.1 Get-Notifications 1
D [14/Apr/2013:11:43:31 -0700] Get-Notifications /
D [14/Apr/2013:11:43:31 -0700] cupsdIsAuthorized: requesting-user-name="mitch"
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 1.1 Get-Notifications 1
D [14/Apr/2013:11:43:31 -0700] Get-Notifications /
D [14/Apr/2013:11:43:31 -0700] cupsdIsAuthorized: requesting-user-name="mitch"
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 35
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Printer-Attributes ipp://localhost/printers/Canon_MF3010
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_MF3010) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 30 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 35 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 1.1 Get-Printer-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Printer-Attributes 
D [14/Apr/2013:11:43:31 -0700] Get-Printer-Attributes client-error-not-found: The printer or class does not exist.
D [14/Apr/2013:11:43:31 -0700] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 36 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 36 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 36 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 36 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 36
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 35
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 35 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 35
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAcceptClient: 35 from localhost (Domain)
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 35 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 35
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Printer-Attributes ipp://localhost/printers/Canon_MF3010
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_MF3010) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 30 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 30
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [14/Apr/2013:11:43:31 -0700] Get-Printer-Attributes ipp://localhost/printers/Canon_MF3010
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_MF3010) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 34 WAITING Closing on EOF
D [14/Apr/2013:11:43:31 -0700] cupsdCloseClient: 34
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Classes
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Classes
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:31 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:31 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:31 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:31 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:31 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [14/Apr/2013:11:43:36 -0700] [Job 15] Before page loop - %%Page: 1 1
D [14/Apr/2013:11:43:36 -0700] [Job 15] Copying page 1...
D [14/Apr/2013:11:43:36 -0700] [Job 14] Unloading...
D [14/Apr/2013:11:43:36 -0700] [Job 15] pagew = 583.7, pagel = 763.7
D [14/Apr/2013:11:43:36 -0700] [Job 15] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [14/Apr/2013:11:43:36 -0700] [Job 15] PageLeft = 14.2, PageRight = 597.8
D [14/Apr/2013:11:43:36 -0700] [Job 15] PageTop = 777.8, PageBottom = 14.2
D [14/Apr/2013:11:43:36 -0700] [Job 15] PageWidth = 612.0, PageLength = 792.0
D [14/Apr/2013:11:43:36 -0700] [Job 15] opvpOpenPrinter(463)
D [14/Apr/2013:11:43:36 -0700] [Job 15] Can't exec driver program
D [14/Apr/2013:11:43:36 -0700] [Job 15] Can't receive READY message
D [14/Apr/2013:11:43:36 -0700] PID 2147 (/usr/lib/cups/filter/pstoufr2cpca) did not catch or ignore signal 13.
D [14/Apr/2013:11:43:36 -0700] PID 2148 (/usr/lib/cups/backend/usb) exited with no errors.
D [14/Apr/2013:11:43:36 -0700] [Job 15] Wrote 1 pages...
D [14/Apr/2013:11:43:36 -0700] PID 2146 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [14/Apr/2013:11:43:36 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
I [14/Apr/2013:11:43:36 -0700] [Job 15] Job completed.
D [14/Apr/2013:11:43:36 -0700] cupsdMarkDirty(----J-)
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdMarkDirty(-----S)
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:36 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:36 -0700] [Notifier] JobCompleted
D [14/Apr/2013:11:43:36 -0700] cupsdAcceptClient: 30 from localhost (Domain)
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Printing jobs and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] [Notifier] state=3
D [14/Apr/2013:11:43:36 -0700] [Notifier] PrinterStateChanged
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 30 1.1 Get-Job-Attributes 1
D [14/Apr/2013:11:43:36 -0700] Get-Job-Attributes ipp://localhost/jobs/15
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAcceptClient: 31 from localhost (Domain)
D [14/Apr/2013:11:43:36 -0700] cupsdAcceptClient: 34 from localhost (Domain)
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 31 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 31 1.1 Get-Notifications 1
D [14/Apr/2013:11:43:36 -0700] Get-Notifications /
D [14/Apr/2013:11:43:36 -0700] cupsdIsAuthorized: requesting-user-name="mitch"
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAcceptClient: 35 from localhost (Domain)
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 35 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 34 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 35 1.1 Get-Notifications 1
D [14/Apr/2013:11:43:36 -0700] Get-Notifications /
D [14/Apr/2013:11:43:36 -0700] cupsdIsAuthorized: requesting-user-name="mitch"
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdAcceptClient: 36 from localhost (Domain)
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 34 1.1 Get-Notifications 1
D [14/Apr/2013:11:43:36 -0700] Get-Notifications /
D [14/Apr/2013:11:43:36 -0700] cupsdIsAuthorized: requesting-user-name="mitch"
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 36 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 36 1.1 Get-Printer-Attributes 1
D [14/Apr/2013:11:43:36 -0700] Get-Printer-Attributes ipp://mitch-Inspiron-3520/printers/Canon_MF3010
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://mitch-Inspiron-3520/printers/Canon_MF3010) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 31 WAITING Closing on EOF
D [14/Apr/2013:11:43:36 -0700] cupsdCloseClient: 31
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 34 WAITING Closing on EOF
D [14/Apr/2013:11:43:36 -0700] cupsdCloseClient: 34
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [14/Apr/2013:11:43:36 -0700] Get-Printer-Attributes ipp://localhost/printers/Canon_MF3010
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_MF3010) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 35 WAITING Closing on EOF
D [14/Apr/2013:11:43:36 -0700] cupsdCloseClient: 35
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Classes
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Printers
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Classes
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdAuthorize: No authentication data provided.
D [14/Apr/2013:11:43:36 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [14/Apr/2013:11:43:36 -0700] CUPS-Get-Default
D [14/Apr/2013:11:43:36 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [14/Apr/2013:11:43:36 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
I [14/Apr/2013:11:44:01 -0700] Saving job.cache...
I [14/Apr/2013:11:44:03 -0700] Saving subscriptions.conf...
D [14/Apr/2013:11:44:04 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
D [14/Apr/2013:11:44:04 -0700] Report: clients=16
D [14/Apr/2013:11:44:04 -0700] Report: jobs=15
D [14/Apr/2013:11:44:04 -0700] Report: jobs-active=0
D [14/Apr/2013:11:44:04 -0700] Report: printers=1
D [14/Apr/2013:11:44:04 -0700] Report: printers-implicit=0
D [14/Apr/2013:11:44:04 -0700] Report: stringpool-string-count=5659
D [14/Apr/2013:11:44:04 -0700] Report: stringpool-alloc-bytes=10760
D [14/Apr/2013:11:44:04 -0700] Report: stringpool-total-bytes=118312
D [14/Apr/2013:11:44:58 -0700] [Job 15] Unloading...

---

### Post by pdc on 2013-04-14
when I google on 

> cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"

I get threads such as this

[http://ubuntuforums.org/showthread.php?t=2054048](http://ubuntuforums.org/showthread.php?t=2054048)

I leave it to you to read up on this;

I have a belief that you should install a new small partition of the 32bit Ubuntu 13.04 that is due in about a week; and install the 32bit drivers for this printer; and see how you get along

---


---
title: "Lexmark pro905, driver installed but printer not recognized."
date: 2011-10-15
forum: Hardware
---

### Post by Black_Sector on 2011-10-15
I dont see a printer when I try to print something out. Nothing happens at all, and I am sure I installed the driver right from the website. Is there a tool I can use to connect to the printer if the driver theoretically works?

There is also a "toolbox", but it does not work. It says it requires authentication but the box for that is blank.


Is there a way to run that app in the terminal?

The printer is great, but its too much trouble without Linux support. I really wish the drivers would just work out of the box in Ubuntu.....maybe next time.

---

### Post by Black_Sector on 2011-10-15
OK, I added some gnome tools, and its recognized now, but I am still getting errors.

```
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Not busy
D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients
D [14/Oct/2011:22:01:37 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 1.1 Get-Jobs 1
D [14/Oct/2011:22:01:37 -0700] Get-Jobs ipp://localhost/printers/
D [14/Oct/2011:22:01:37 -0700] [Job 8] Loading attributes...
D [14/Oct/2011:22:01:37 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Not busy
D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients
D [14/Oct/2011:22:01:37 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 1.1 Get-Jobs 1
D [14/Oct/2011:22:01:37 -0700] Get-Jobs ipp://localhost/printers/
D [14/Oct/2011:22:01:37 -0700] [Job 4] Loading attributes...
D [14/Oct/2011:22:01:37 -0700] [Job 6] Loading attributes...
D [14/Oct/2011:22:01:37 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Not busy
D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients
D [14/Oct/2011:22:01:37 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 1.1 Create-Printer-Subscription 1
D [14/Oct/2011:22:01:37 -0700] Create-Printer-Subscription /
D [14/Oct/2011:22:01:37 -0700] cupsdCreateSubscription(con=0x7fefabe9fc80(25), uri="/")
D [14/Oct/2011:22:01:37 -0700] pullmethod="ippget"
D [14/Oct/2011:22:01:37 -0700] notify-lease-duration=86400
D [14/Oct/2011:22:01:37 -0700] notify-time-interval=0
D [14/Oct/2011:22:01:37 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [14/Oct/2011:22:01:37 -0700] Added subscription 8 for server
D [14/Oct/2011:22:01:37 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:37 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:39 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:39 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:39 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:39 -0700] cupsdReadClient: 25 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:39 -0700] Get-Notifications /
D [14/Oct/2011:22:01:39 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:39 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:39 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "wlan0" = 192.168.1.101:631
D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "wlan0" = [v1.fe80::8a25:2cff:fe6f:4361+wlan0]:631
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 26 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 26 POST /printers/Pro800-Pro900-Series HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 26 1.1 Print-Job 1
D [14/Oct/2011:22:01:43 -0700] Print-Job ipp://localhost/printers/Pro800-Pro900-Series
D [14/Oct/2011:22:01:43 -0700] [Job ???] Auto-typing file...
I [14/Oct/2011:22:01:43 -0700] [Job ???] Request file type is application/vnd.cups-banner.
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)
D [14/Oct/2011:22:01:43 -0700] add_job: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Adding default job-sheets values "none,none"...
I [14/Oct/2011:22:01:43 -0700] [Job 9] Adding start banner page "none".
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)
I [14/Oct/2011:22:01:43 -0700] [Job 9] Adding end banner page "none".
I [14/Oct/2011:22:01:43 -0700] [Job 9] File of type application/vnd.cups-banner queued by "user".
D [14/Oct/2011:22:01:43 -0700] [Job 9] hold_until=0
I [14/Oct/2011:22:01:43 -0700] [Job 9] Queued on "Pro800-Pro900-Series" by "user".
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:43 -0700] [Job 9] job-sheets=none,none
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[0]="Pro800-Pro900-Series"
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[1]="9"
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[2]="user"
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[3]="Test Page"
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[4]="1"
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[5]="job-uuid=urn:uuid:360d6746-e370-3f34-5245-3be63b967c78 fitplot orientation-requested=3 job-originating-host-name=localhost time-at-creation=1318654903 time-at-processing=1318654903 AP_D_InputSlot="
D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[6]="/var/spool/cups/d00009-001"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[8]="HOME=/var/spool/cups/tmp"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[10]="SERVER_ADMIN=root@pc"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[11]="SOFTWARE=CUPS/1.4.6"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[13]="USER=root"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[16]="IPP_PORT=631"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[17]="CHARSET=utf-8"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[18]="LANG=en_US.UTF-8"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[19]="PPD=/etc/cups/ppd/Pro800-Pro900-Series.ppd"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[20]="RIP_MAX_CACHE=auto"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[22]="DEVICE_URI=usb://Lexmark/Pro800-Pro900%20Series"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[23]="PRINTER_INFO=Lexmark Pro800-Pro900 Series"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[24]="PRINTER_LOCATION=pc"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[25]="PRINTER=Pro800-Pro900-Series"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[26]="CUPS_FILETYPE=document"
D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[27]="FINAL_CONTENT_TYPE=printer/Pro800-Pro900-Series"
I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/bannertops (PID 11333)
I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/pstopdf (PID 11334)
I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 11335)
I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 11336)
I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/local/lexmark/legacy/bin/printfilter (PID 11337)
I [14/Oct/2011:22:01:43 -0700] [Job 9] Started backend /usr/lib/cups/backend/usb (PID 11339)
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Pro800-Pro900-Series) from localhost
D [14/Oct/2011:22:01:43 -0700] [Job 9] pstopdf 5 args: 9 user Test Page 1 job-uuid=urn:uuid:360d6746-e370-3f34-5245-3be63b967c78 fitplot orientation-requested=3 job-originating-host-name=localhost time-at-creation=1318654903 time-at-processing=1318654903 AP_D_InputSlot=
D [14/Oct/2011:22:01:43 -0700] [Job 9] PPD: /etc/cups/ppd/Pro800-Pro900-Series.ppd
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] [Job 9] load_banner(filename="/var/spool/cups/d00009-001")
D [14/Oct/2011:22:01:43 -0700] [Job 9] Page = 612x792; 18,36 to 594,787
D [14/Oct/2011:22:01:43 -0700] [Job 9] STATE: +connecting-to-device
D [14/Oct/2011:22:01:43 -0700] [Job 9] /usr/local/lexmark/legacy/bin/printfilter: Permission denied
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:43 -0700] PID 11337 (/usr/local/lexmark/legacy/bin/printfilter) stopped with status 22!
D [14/Oct/2011:22:01:43 -0700] [Job 9] Printer using device file "/dev/usblp0"...
D [14/Oct/2011:22:01:43 -0700] [Job 9] STATE: -connecting-to-device
D [14/Oct/2011:22:01:43 -0700] [Job 9] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0x7feea23c3e10)
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:43 -0700] PID 11339 (/usr/lib/cups/backend/usb) exited with no errors.
D [14/Oct/2011:22:01:43 -0700] [Job 9] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [14/Oct/2011:22:01:43 -0700] [Job 9] PNG image: 192x128x8, color_type=2 (RGB)
D [14/Oct/2011:22:01:43 -0700] PID 11333 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [14/Oct/2011:22:01:43 -0700] [Job 9] Resolution:
D [14/Oct/2011:22:01:43 -0700] [Job 9] Page size: Letter
D [14/Oct/2011:22:01:43 -0700] [Job 9] Width: 612.00, height: 792.00, absolute margins: 18.00, 36.00, 594.00, 787.20
D [14/Oct/2011:22:01:43 -0700] [Job 9] Relative margins: 18.00, 36.00, 18.00, 4.80
D [14/Oct/2011:22:01:43 -0700] [Job 9] PPD options: -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00
D [14/Oct/2011:22:01:43 -0700] [Job 9] PostScript to be injected:
D [14/Oct/2011:22:01:43 -0700] [Job 9] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 -sOutputFile=-  -c .setpdfwrite -f -
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 29 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 29
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 29 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 29
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Classes
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Default
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [14/Oct/2011:22:01:43 -0700] PID 11334 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [14/Oct/2011:22:01:43 -0700] PID 11335 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [14/Oct/2011:22:01:43 -0700] PID 11336 (/usr/lib/cups/filter/pdftoraster-poppler) did not catch or ignore signal 13.
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
E [14/Oct/2011:22:01:43 -0700] [Job 9] Job stopped due to filter errors; please consult the error_log file for details.
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)
D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 27
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 29 from localhost (Domain)
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Printer-Attributes ipp://pc:631/printers/Pro800-Pro900-Series
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://pc:631/printers/Pro800-Pro900-Series) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 27
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 1.1 Get-Notifications 1
D [14/Oct/2011:22:01:43 -0700] Get-Notifications /
D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Classes
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Default
D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:44 -0700] [Job 9] Unloading...
D [14/Oct/2011:22:01:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [14/Oct/2011:22:01:48 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:48 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:48 -0700] cupsdReadClient: 25 1.1 Cancel-Subscription 1
D [14/Oct/2011:22:01:48 -0700] Cancel-Subscription /
D [14/Oct/2011:22:01:48 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:01:48 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:48 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [14/Oct/2011:22:01:48 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [14/Oct/2011:22:01:49 -0700] [Job 1] Unloading...
D [14/Oct/2011:22:01:49 -0700] [Job 2] Unloading...
D [14/Oct/2011:22:01:49 -0700] [Job 3] Unloading...
D [14/Oct/2011:22:01:49 -0700] [Job 5] Unloading...
D [14/Oct/2011:22:01:49 -0700] [Job 7] Unloading...
D [14/Oct/2011:22:01:49 -0700] Report: clients=14
D [14/Oct/2011:22:01:49 -0700] Report: jobs=9
D [14/Oct/2011:22:01:49 -0700] Report: jobs-active=7
D [14/Oct/2011:22:01:49 -0700] Report: printers=2
D [14/Oct/2011:22:01:49 -0700] Report: printers-implicit=0
D [14/Oct/2011:22:01:49 -0700] Report: stringpool-string-count=29520
D [14/Oct/2011:22:01:49 -0700] Report: stringpool-alloc-bytes=15936
D [14/Oct/2011:22:01:49 -0700] Report: stringpool-total-bytes=544304
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 27
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 24 WAITING Closing on EOF
D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 24
D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 24 from localhost (Domain)
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 24 POST / HTTP/1.1
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 24 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:49 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series
D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 20 WAITING Closing on EOF
D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 20
D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 20 from localhost (Domain)
D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:49 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:49 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series
D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 27
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 WAITING Closing on EOF
D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 19
D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 19 from localhost (Domain)
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:49 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [14/Oct/2011:22:01:49 -0700] CUPS-Get-Default
D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:50 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:50 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:50 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:50 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:50 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:51 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:51 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:51 -0700] cupsdReadClient: 27 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:51 -0700] Get-Printer-Attributes ipp://localhost/printers/PDF
D [14/Oct/2011:22:01:51 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF) from localhost
D [14/Oct/2011:22:01:51 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:51 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 30 from localhost (Domain)
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [14/Oct/2011:22:01:54 -0700] cupsdCloseClient: 28
D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 31 from localhost (Domain)
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [14/Oct/2011:22:01:54 -0700] cupsdCloseClient: 27
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 POST / HTTP/1.1
D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:54 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:54 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:54 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 POST / HTTP/1.1
D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:54 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:54 -0700] Get-Printer-Attributes ipp://localhost/printers/PDF
D [14/Oct/2011:22:01:54 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF) from localhost
D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 19 WAITING Closing on EOF
D [14/Oct/2011:22:01:54 -0700] cupsdCloseClient: 19
D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:55 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:55 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:55 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:55 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Default 1
D [14/Oct/2011:22:01:55 -0700] CUPS-Get-Default
D [14/Oct/2011:22:01:55 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:55 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:55 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:55 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 19 from localhost (Domain)
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [14/Oct/2011:22:01:58 -0700] CUPS-Get-Printers
D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:58 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series
D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 WAITING Closing on EOF
D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 19
D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 19 from localhost (Domain)
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 20 WAITING Closing on EOF
D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 20
D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 20 from localhost (Domain)
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 24 WAITING Closing on EOF
D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 24
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 20 POST / HTTP/1.1
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1
D [14/Oct/2011:22:01:58 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series
D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 24 from localhost (Domain)
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 24 WAITING Closing on EOF
D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 24
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 1.1 Get-Jobs 1
D [14/Oct/2011:22:01:58 -0700] Get-Jobs ipp://localhost/printers/
D [14/Oct/2011:22:01:58 -0700] [Job 1] Loading attributes...
D [14/Oct/2011:22:01:58 -0700] [Job 2] Loading attributes...
D [14/Oct/2011:22:01:58 -0700] [Job 3] Loading attributes...
D [14/Oct/2011:22:01:58 -0700] [Job 5] Loading attributes...
D [14/Oct/2011:22:01:58 -0700] [Job 7] Loading attributes...
D [14/Oct/2011:22:01:58 -0700] [Job 9] Loading attributes...
D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 1.1 Get-Jobs 1
D [14/Oct/2011:22:01:58 -0700] Get-Jobs ipp://localhost/printers/
D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 1.1 Create-Printer-Subscription 1
D [14/Oct/2011:22:01:58 -0700] Create-Printer-Subscription /
D [14/Oct/2011:22:01:58 -0700] cupsdCreateSubscription(con=0x7fefabf11370(30), uri="/")
D [14/Oct/2011:22:01:58 -0700] pullmethod="ippget"
D [14/Oct/2011:22:01:58 -0700] notify-lease-duration=86400
D [14/Oct/2011:22:01:58 -0700] notify-time-interval=0
D [14/Oct/2011:22:01:58 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [14/Oct/2011:22:01:58 -0700] Added subscription 9 for server
D [14/Oct/2011:22:01:58 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:02:00 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Oct/2011:22:02:00 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:02:00 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:02:00 -0700] cupsdReadClient: 30 1.1 Get-Notifications 1
D [14/Oct/2011:22:02:00 -0700] Get-Notifications /
D [14/Oct/2011:22:02:00 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:02:00 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2011:22:02:00 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:02:05 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 1.1 Get-Job-Attributes 1
D [14/Oct/2011:22:02:05 -0700] Get-Job-Attributes ipp://localhost/jobs/9
D [14/Oct/2011:22:02:05 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 POST / HTTP/1.1
D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:02:05 -0700] cupsdAuthorize: No authentication data provided.
D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 1.1 Cancel-Subscription 1
D [14/Oct/2011:22:02:05 -0700] Cancel-Subscription /
D [14/Oct/2011:22:02:05 -0700] cupsdIsAuthorized: requesting-user-name="user"
D [14/Oct/2011:22:02:05 -0700] cupsdMarkDirty(-----S)
D [14/Oct/2011:22:02:05 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Dirty files
D [14/Oct/2011:22:02:05 -0700] cupsdAcceptClient: 24 from localhost (Domain)
D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 24 GET /admin/log/error_log HTTP/1.1
D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2011:22:02:05 -0700] cupsdAuthorize: No authentication data provided.
```

---

### Post by Black_Sector on 2011-10-15
It says CUPS connection failure, even though the printer is recognized now.

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Pro800-Pro900-Series>,
 'cups_instance': None,
 'cups_queue': 'Pro800-Pro900-Series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/Pro800-Pro900%20Series',
                       'printer-info': u'Lexmark Pro800-Pro900 Series',
                       'printer-is-shared': True,
                       'printer-location': u'pc',
                       'printer-make-and-model': u'Lexmark Pro800-Pro900 Series, 1.0',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/local/lexmark/legacy/bin/printfilter failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 61468,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Pro800-Pro900-Series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.6',
                                 'device-uri': u'usb://Lexmark/Pro800-Pro900%20Series',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.adobe-reader-postscript',
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
                                 'fitplot-default': True,
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
                                 'media-bottom-margin-supported': [1270, 0],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-left-margin-supported': [635, 338],
                                 'media-right-margin-supported': [635,
                                                                  338,
                                                                  169,
                                                                  317],
                                 'media-source-supported': [u'auto',
                                                            u'tray1',
                                                            u'tray2'],
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'om_letter-bl_229.3x305.5mm',
                                                     u'oe_letter-ba_8.5x110in',
                                                     u'na_legal_8.5x14in',
                                                     u'oe_legal-bl_9x15in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a4_210x297mm',
                                                     u'om_a4-bl_217.38x323.07mm',
                                                     u'om_a4-ba_209.97x2970.03mm',
                                                     u'iso_a5_148x210mm',
                                                     u'om_a5-bl_155.43x236.07mm',
                                                     u'om_b5-jis_182.03x256.96mm',
                                                     u'om_b5-jisbl_189.51x283.06mm',
                                                     u'om_envelope10_104.77x241.3mm',
                                                     u'om_envelope9_100.89x225.42mm',
                                                     u'om_envelope734_98.42x190.5mm',
                                                     u'om_envelope634_92.07x165.1mm',
                                                     u'om_envelope-a2_111.12x146.05mm',
                                                     u'om_envelope-b5_176.03x249.97mm',
                                                     u'om_envelope-c6_114.44x161.92mm',
                                                     u'om_envelope-dl_110.06x220.02mm',
                                                     u'om_envelope-chokei3_120.01x234.95mm',
                                                     u'om_envelope-chokei4_89.97x205.1mm',
                                                     u'om_envelope-chokei40_89.95x225mm',
                                                     u'om_envelope-kakugata3_216.04x277mm',
                                                     u'om_envelope-kakugata4_197.02x266.99mm',
                                                     u'om_envelope-kakugata5_190x240.03mm',
                                                     u'om_envelope-kakugata6_161.92x229.02mm',
                                                     u'oe_card3x5_3x5in',
                                                     u'om_card-a6_104.98x147.95mm',
                                                     u'om_card-a6-bl_112.46x174.06mm',
                                                     u'om_postcard-hagaki_100.01x147.95mm',
                                                     u'om_postcard-hagaki-bl_107.49x174.06mm',
                                                     u'om_photo312x5_88.85x127mm',
                                                     u'om_photo312x5-bl_96.33x153.1mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'om_4x6-bl_109.07x178.5mm',
                                                     u'om_100x200mm_100x200mm',
                                                     u'om_4x8-bl_109.07x229.3mm',
                                                     u'oe_photo5x7_5x7in',
                                                     u'om_photo5x7-bl_134.47x203.9mm',
                                                     u'om_photo-l_89.04x127mm',
                                                     u'om_photo-lbl_96.52x153.1mm',
                                                     u'om_photo2-l_127x178.01mm',
                                                     u'om_100x150mm_100x150mm',
                                                     u'om_10x15cm-bl_109.07x178.85mm',
                                                     u'om_130x180mm_130x180mm',
                                                     u'om_13x18cm-bl_134.47x204.32mm',
                                                     u'custom_min_3x5in',
                                                     u'custom_max_8.5x17in'],
                                 'media-top-margin-supported': [169,
                                                                1270,
                                                                0,
                                                                63,
                                                                204],
                                 'media-type-supported': [u'auto',
                                                          u'stationery',
                                                          u'multi-purpose',
                                                          u'stationery-inkjet',
                                                          u'lxphoto',
                                                          u'lxperfectfinish',
                                                          u'photographic-glossy',
                                                          u'heavy-weight-matte',
                                                          u'photographic-glossy',
                                                          u'transparency',
                                                          u'avery-business',
                                                          u'business',
                                                          u'cardstock',
                                                          u'avery-label',
                                                          u'specialty-label',
                                                          u'cdlabel',
                                                          u'iron-on'],
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
                                 'orientation-requested-default': 3,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-up',
                                 'output-bin-supported': [u'face-up'],
                                 'output-mode-default': u'color',
                                 'output-mode-supported': [u'monochrome',
                                                           u'color'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 15,
                                 'pages-per-minute-color': 15,
                                 'pdl-override-supported': [u'attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': u'none',
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-dns-sd-name': u'Lexmark Pro800-Pro900 Series @ pc',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-icons': u'http://localhost:631/icons/Pro800-Pro900-Series.png',
                                 'printer-info': u'Lexmark Pro800-Pro900 Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'pc',
                                 'printer-make-and-model': u'Lexmark Pro800-Pro900 Series, 1.0',
                                 'printer-more-info': u'http://localhost:631/printers/Pro800-Pro900-Series',
                                 'printer-name': u'Pro800-Pro900-Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': '(unknown IPP tag)',
                                 'printer-resolution-supported': '(unknown IPP tag)',
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1318654903,
                                 'printer-state-message': u'/usr/local/lexmark/legacy/bin/printfilter failed',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 61468,
                                 'printer-up-time': 1318654918,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Pro800-Pro900-Series'],
                                 'queued-job-count': 7,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'ColorModel': u'AllColors',
                                            u'DupDryTime': u'UsePrinterSettings',
                                            u'Duplex': u'UsePrinterSettings',
                                            u'InputSlot': u'Automatic',
                                            u'MediaType': u'Automatic',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintMirror': u'True',
                                            u'PrintQuality': u'Automatic',
                                            u'Sharpening': u'2'},
                               u'InstallableOptions': {u'Tray2': u'True'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 83585}
Page 7 (Print test page):
{'test_page_attempted': '14/Oct/2011:22:01:43 +0000',
 'test_page_job_id': [9],
 'test_page_job_status': [(False,
                           1,
                           'Pro800-Pro900-Series',
                           'Test Page',
                           'Stopped',
                           None),
                          (False,
                           2,
                           'Pro800-Pro900-Series',
                           "[Phoronix] Lexmark's Linux Secret (Testing With The Pro905 Platinum)",
                           'Stopped',
                           None),
                          (False,
                           3,
                           'Pro800-Pro900-Series',
                           '[xubuntu] Lexmark pro905, driver installed but printer not recognized. - Ubuntu Forums',
                           'Stopped',
                           None),
                          (False,
                           5,
                           'Pro800-Pro900-Series',
                           'Test Page',
                           'Stopped',
                           None),
                          (False,
                           7,
                           'Pro800-Pro900-Series',
                           '[xubuntu] Lexmark pro905, driver installed but printer not recognized. - Ubuntu Forums',
                           'Stopped',
                           None),
                          (False,
                           8,
                           'Pro800-Pro900-Series',
                           'Test Page',
                           'Stopped',
                           None),
                          (True,
                           9,
                           'Pro800-Pro900-Series',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'fitplot': True,
                            'job-hold-until': u'no-hold',
                            'job-id': 9,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/9',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'user',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/local/lexmark/legacy/bin/printfilter failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1318654925,
                            'job-printer-uri': u'ipp://pc:631/printers/Pro800-Pro900-Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/9',
                            'job-uuid': u'urn:uuid:360d6746-e370-3f34-5245-3be63b967c78',
                            'orientation-requested': 3,
                            'printer-uri': u'ipp://localhost/printers/Pro800-Pro900-Series',
                            'time-at-completed': None,
                            'time-at-creation': 1318654903,
                            'time-at-processing': 1318654903})],
 'test_page_successful': False}
Page 8 (Error log fetch):
{'error_log': ['D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Not busy',
               'D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients',
               'D [14/Oct/2011:22:01:37 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 1.1 Get-Jobs 1',
               'D [14/Oct/2011:22:01:37 -0700] Get-Jobs ipp://localhost/printers/',
               'D [14/Oct/2011:22:01:37 -0700] [Job 8] Loading attributes...',
               'D [14/Oct/2011:22:01:37 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Not busy',
               'D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients',
               'D [14/Oct/2011:22:01:37 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 1.1 Get-Jobs 1',
               'D [14/Oct/2011:22:01:37 -0700] Get-Jobs ipp://localhost/printers/',
               'D [14/Oct/2011:22:01:37 -0700] [Job 4] Loading attributes...',
               'D [14/Oct/2011:22:01:37 -0700] [Job 6] Loading attributes...',
               'D [14/Oct/2011:22:01:37 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Not busy',
               'D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients',
               'D [14/Oct/2011:22:01:37 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:37 -0700] cupsdReadClient: 25 1.1 Create-Printer-Subscription 1',
               'D [14/Oct/2011:22:01:37 -0700] Create-Printer-Subscription /',
               'D [14/Oct/2011:22:01:37 -0700] cupsdCreateSubscription(con=0x7fefabe9fc80(25), uri="/")',
               'D [14/Oct/2011:22:01:37 -0700] pullmethod="ippget"',
               'D [14/Oct/2011:22:01:37 -0700] notify-lease-duration=86400',
               'D [14/Oct/2011:22:01:37 -0700] notify-time-interval=0',
               'D [14/Oct/2011:22:01:37 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [14/Oct/2011:22:01:37 -0700] Added subscription 8 for server',
               'D [14/Oct/2011:22:01:37 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:37 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [14/Oct/2011:22:01:37 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:39 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:39 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:39 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:39 -0700] cupsdReadClient: 25 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:39 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:39 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:39 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:39 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "wlan0" = 192.168.1.101:631',
               'D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [14/Oct/2011:22:01:42 -0700] cupsdNetIFUpdate: "wlan0" = [v1.fe80::8a25:2cff:fe6f:4361+wlan0]:631',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 26 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 26 POST /printers/Pro800-Pro900-Series HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 26 1.1 Print-Job 1',
               'D [14/Oct/2011:22:01:43 -0700] Print-Job ipp://localhost/printers/Pro800-Pro900-Series',
               'D [14/Oct/2011:22:01:43 -0700] [Job ???] Auto-typing file...',
               'I [14/Oct/2011:22:01:43 -0700] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)',
               'D [14/Oct/2011:22:01:43 -0700] add_job: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Adding default job-sheets values "none,none"...',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Adding start banner page "none".',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Adding end banner page "none".',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] File of type application/vnd.cups-banner queued by "user".',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] hold_until=0',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Queued on "Pro800-Pro900-Series" by "user".',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] job-sheets=none,none',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[0]="Pro800-Pro900-Series"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[1]="9"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[2]="user"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[3]="Test Page"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[4]="1"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[5]="job-uuid=urn:uuid:360d6746-e370-3f34-5245-3be63b967c78 fitplot orientation-requested=3 job-originating-host-name=localhost time-at-creation=1318654903 time-at-processing=1318654903 AP_D_InputSlot="',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] argv[6]="/var/spool/cups/d00009-001"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[10]="SERVER_ADMIN=root@pc"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[11]="SOFTWARE=CUPS/1.4.6"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[13]="USER=root"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[16]="IPP_PORT=631"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[17]="CHARSET=utf-8"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[18]="LANG=en_US.UTF-8"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[19]="PPD=/etc/cups/ppd/Pro800-Pro900-Series.ppd"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[20]="RIP_MAX_CACHE=auto"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[22]="DEVICE_URI=usb://Lexmark/Pro800-Pro900%20Series"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[23]="PRINTER_INFO=Lexmark Pro800-Pro900 Series"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[24]="PRINTER_LOCATION=pc"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[25]="PRINTER=Pro800-Pro900-Series"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[26]="CUPS_FILETYPE=document"',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] envp[27]="FINAL_CONTENT_TYPE=printer/Pro800-Pro900-Series"',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/bannertops (PID 11333)',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/pstopdf (PID 11334)',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 11335)',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 11336)',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Started filter /usr/local/lexmark/legacy/bin/printfilter (PID 11337)',
               'I [14/Oct/2011:22:01:43 -0700] [Job 9] Started backend /usr/lib/cups/backend/usb (PID 11339)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Pro800-Pro900-Series) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] pstopdf 5 args: 9 user Test Page 1 job-uuid=urn:uuid:360d6746-e370-3f34-5245-3be63b967c78 fitplot orientation-requested=3 job-originating-host-name=localhost time-at-creation=1318654903 time-at-processing=1318654903 AP_D_InputSlot=',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] PPD: /etc/cups/ppd/Pro800-Pro900-Series.ppd',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] load_banner(filename="/var/spool/cups/d00009-001")',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Page = 612x792; 18,36 to 594,787',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] STATE: +connecting-to-device',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] /usr/local/lexmark/legacy/bin/printfilter: Permission denied',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:43 -0700] PID 11337 (/usr/local/lexmark/legacy/bin/printfilter) stopped with status 22!',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Printer using device file "/dev/usblp0"...',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] STATE: -connecting-to-device',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0x7feea23c3e10)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:43 -0700] PID 11339 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [14/Oct/2011:22:01:43 -0700] PID 11333 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Resolution:',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Page size: Letter',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Width: 612.00, height: 792.00, absolute margins: 18.00, 36.00, 594.00, 787.20',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Relative margins: 18.00, 36.00, 18.00, 4.80',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] PPD options: -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] PostScript to be injected:',
               'D [14/Oct/2011:22:01:43 -0700] [Job 9] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 -sOutputFile=-  -c .setpdfwrite -f -',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 29 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 29',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 29 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 29',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Classes',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Default',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] PID 11334 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [14/Oct/2011:22:01:43 -0700] PID 11335 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [14/Oct/2011:22:01:43 -0700] PID 11336 (/usr/lib/cups/filter/pdftoraster-poppler) did not catch or ignore signal 13.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'E [14/Oct/2011:22:01:43 -0700] [Job 9] Job stopped due to filter errors; please consult the error_log file for details.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(----J-)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 27',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAcceptClient: 29 from localhost (Domain)',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Printer-Attributes ipp://pc:631/printers/Pro800-Pro900-Series',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://pc:631/printers/Pro800-Pro900-Series) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 29 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 27 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 27',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 25 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:01:43 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:01:43 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:43 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Classes',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:43 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [14/Oct/2011:22:01:43 -0700] CUPS-Get-Default',
               'D [14/Oct/2011:22:01:43 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [14/Oct/2011:22:01:43 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:44 -0700] [Job 9] Unloading...',
               'D [14/Oct/2011:22:01:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:48 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:48 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:48 -0700] cupsdReadClient: 25 1.1 Cancel-Subscription 1',
               'D [14/Oct/2011:22:01:48 -0700] Cancel-Subscription /',
               'D [14/Oct/2011:22:01:48 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:01:48 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:48 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [14/Oct/2011:22:01:48 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [14/Oct/2011:22:01:49 -0700] [Job 1] Unloading...',
               'D [14/Oct/2011:22:01:49 -0700] [Job 2] Unloading...',
               'D [14/Oct/2011:22:01:49 -0700] [Job 3] Unloading...',
               'D [14/Oct/2011:22:01:49 -0700] [Job 5] Unloading...',
               'D [14/Oct/2011:22:01:49 -0700] [Job 7] Unloading...',
               'D [14/Oct/2011:22:01:49 -0700] Report: clients=14',
               'D [14/Oct/2011:22:01:49 -0700] Report: jobs=9',
               'D [14/Oct/2011:22:01:49 -0700] Report: jobs-active=7',
               'D [14/Oct/2011:22:01:49 -0700] Report: printers=2',
               'D [14/Oct/2011:22:01:49 -0700] Report: printers-implicit=0',
               'D [14/Oct/2011:22:01:49 -0700] Report: stringpool-string-count=29520',
               'D [14/Oct/2011:22:01:49 -0700] Report: stringpool-alloc-bytes=15936',
               'D [14/Oct/2011:22:01:49 -0700] Report: stringpool-total-bytes=544304',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 27',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 24 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 24',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 24 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:49 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series',
               'D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 20',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:49 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:49 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series',
               'D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 27 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 27',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:49 -0700] cupsdCloseClient: 19',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:49 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:49 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1',
               'D [14/Oct/2011:22:01:49 -0700] CUPS-Get-Default',
               'D [14/Oct/2011:22:01:49 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [14/Oct/2011:22:01:49 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:50 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:50 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:50 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:50 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:50 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:50 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:50 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:51 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:51 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:51 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:51 -0700] cupsdReadClient: 27 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:51 -0700] Get-Printer-Attributes ipp://localhost/printers/PDF',
               'D [14/Oct/2011:22:01:51 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF) from localhost',
               'D [14/Oct/2011:22:01:51 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:51 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 28 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:54 -0700] cupsdCloseClient: 28',
               'D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 31 from localhost (Domain)',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 27 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:54 -0700] cupsdCloseClient: 27',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:54 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:54 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:54 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:54 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 31 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:54 -0700] Get-Printer-Attributes ipp://localhost/printers/PDF',
               'D [14/Oct/2011:22:01:54 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF) from localhost',
               'D [14/Oct/2011:22:01:54 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:54 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [14/Oct/2011:22:01:54 -0700] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:54 -0700] cupsdCloseClient: 19',
               'D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:55 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:55 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:55 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:55 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Default 1',
               'D [14/Oct/2011:22:01:55 -0700] CUPS-Get-Default',
               'D [14/Oct/2011:22:01:55 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:55 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:55 -0700] cupsdReadClient: 27 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:55 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:55 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:55 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1',
               'D [14/Oct/2011:22:01:58 -0700] CUPS-Get-Printers',
               'D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:58 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series',
               'D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 19',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 20',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 24 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 24',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1',
               'D [14/Oct/2011:22:01:58 -0700] Get-Printer-Attributes ipp://localhost/printers/Pro800-Pro900-Series',
               'D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Pro800-Pro900-Series) from localhost',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 24 WAITING Closing on EOF',
               'D [14/Oct/2011:22:01:58 -0700] cupsdCloseClient: 24',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 1.1 Get-Jobs 1',
               'D [14/Oct/2011:22:01:58 -0700] Get-Jobs ipp://localhost/printers/',
               'D [14/Oct/2011:22:01:58 -0700] [Job 1] Loading attributes...',
               'D [14/Oct/2011:22:01:58 -0700] [Job 2] Loading attributes...',
               'D [14/Oct/2011:22:01:58 -0700] [Job 3] Loading attributes...',
               'D [14/Oct/2011:22:01:58 -0700] [Job 5] Loading attributes...',
               'D [14/Oct/2011:22:01:58 -0700] [Job 7] Loading attributes...',
               'D [14/Oct/2011:22:01:58 -0700] [Job 9] Loading attributes...',
               'D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 1.1 Get-Jobs 1',
               'D [14/Oct/2011:22:01:58 -0700] Get-Jobs ipp://localhost/printers/',
               'D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:01:58 -0700] cupsdReadClient: 30 1.1 Create-Printer-Subscription 1',
               'D [14/Oct/2011:22:01:58 -0700] Create-Printer-Subscription /',
               'D [14/Oct/2011:22:01:58 -0700] cupsdCreateSubscription(con=0x7fefabf11370(30), uri="/")',
               'D [14/Oct/2011:22:01:58 -0700] pullmethod="ippget"',
               'D [14/Oct/2011:22:01:58 -0700] notify-lease-duration=86400',
               'D [14/Oct/2011:22:01:58 -0700] notify-time-interval=0',
               'D [14/Oct/2011:22:01:58 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [14/Oct/2011:22:01:58 -0700] Added subscription 9 for server',
               'D [14/Oct/2011:22:01:58 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:01:58 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [14/Oct/2011:22:01:58 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:02:00 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [14/Oct/2011:22:02:00 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:02:00 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:02:00 -0700] cupsdReadClient: 30 1.1 Get-Notifications 1',
               'D [14/Oct/2011:22:02:00 -0700] Get-Notifications /',
               'D [14/Oct/2011:22:02:00 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:02:00 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [14/Oct/2011:22:02:00 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:02:05 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 1.1 Get-Job-Attributes 1',
               'D [14/Oct/2011:22:02:05 -0700] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [14/Oct/2011:22:02:05 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost',
               'D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:02:05 -0700] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 30 1.1 Cancel-Subscription 1',
               'D [14/Oct/2011:22:02:05 -0700] Cancel-Subscription /',
               'D [14/Oct/2011:22:02:05 -0700] cupsdIsAuthorized: requesting-user-name="user"',
               'D [14/Oct/2011:22:02:05 -0700] cupsdMarkDirty(-----S)',
               'D [14/Oct/2011:22:02:05 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Dirty files',
               'D [14/Oct/2011:22:02:05 -0700] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [14/Oct/2011:22:02:05 -0700] cupsdReadClient: 24 GET /admin/log/error_log HTTP/1.1',
               'D [14/Oct/2011:22:02:05 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [14/Oct/2011:22:02:05 -0700] cupsdAuthorize: No authentication data provided.']}
Page 9 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

```

---


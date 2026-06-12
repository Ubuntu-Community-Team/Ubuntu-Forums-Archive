---
title: "Canon MF4150 on Karmic 9.10 x86_64"
date: 2010-05-14
forum: Hardware
---

### Post by devilized on 2010-05-14
So I've been using Ubuntu on and off for a while (since Edgy), and I can usually Google my way through the issues I've had, but I'm really stuck on this one. 

I've been trying to get my Canon MF4150 working. It worked great on 9.04, but a kernel update more or less destroyed my install, so I ran a clean install of 9.10. I've been successful in installing the cndrvcups_ufr2-uk_2.00-3_amd drivers (after converting the .rpm's to .deb's using Alien).

After installing the drivers, the printer is successfully recognized and added to the printer list. However, it won't print. It doesn't give any errors or anything. The print job submits, it sits in the queue with the status "processing" for a moment (less than second), and then disappears. 

As far as I can tell, the debug output in the error log thinks that the print job was successful:

```

D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 17 POST /printers/Canon-MF4100-Series HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 17 1.1 Print-Job 1
D [14/May/2010:01:53:19 -0400] Print-Job ipp://localhost/printers/Canon-MF4100-Series
D [14/May/2010:01:53:19 -0400] [Job ???] Auto-typing file...
I [14/May/2010:01:53:19 -0400] [Job ???] Request file type is application/postscript.
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(----J-)
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:19 -0400] add_job: requesting-user-name="ken"
D [14/May/2010:01:53:19 -0400] Adding default job-sheets values "none,none"...
I [14/May/2010:01:53:19 -0400] [Job 58] Adding start banner page "none".
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(----J-)
I [14/May/2010:01:53:19 -0400] [Job 58] Adding end banner page "none".
I [14/May/2010:01:53:19 -0400] [Job 58] File of type application/postscript queued by "ken".
D [14/May/2010:01:53:19 -0400] [Job 58] hold_until=0
I [14/May/2010:01:53:19 -0400] [Job 58] Queued on "Canon-MF4100-Series" by "ken".
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(----J-)
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] [Job 58] job-sheets=none,none
D [14/May/2010:01:53:19 -0400] [Job 58] argv[0]="Canon-MF4100-Series"
D [14/May/2010:01:53:19 -0400] [Job 58] argv[1]="58"
D [14/May/2010:01:53:19 -0400] [Job 58] argv[2]="ken"
D [14/May/2010:01:53:19 -0400] [Job 58] argv[3]="Test Page"
D [14/May/2010:01:53:19 -0400] [Job 58] argv[4]="1"
D [14/May/2010:01:53:19 -0400] [Job 58] argv[5]="PageSize=Letter job-uuid=urn:uuid:41b6a095-8c05-3c0b-5dc7-378dec893a8b job-originating-host-name=localhost"
D [14/May/2010:01:53:19 -0400] [Job 58] argv[6]="/var/spool/cups/d00058-001"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[8]="HOME=/var/spool/cups/tmp"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[10]="SERVER_ADMIN=root@hyerk-ubuntu"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[11]="SOFTWARE=CUPS/1.4.1"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[13]="TZ=US/Eastern"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[14]="USER=root"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[17]="IPP_PORT=631"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[18]="CHARSET=utf-8"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[19]="LANG=en_US.UTF-8"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[20]="PPD=/etc/cups/ppd/Canon-MF4100-Series.ppd"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[21]="RIP_MAX_CACHE=1014953k"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[22]="CONTENT_TYPE=application/postscript"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[23]="DEVICE_URI=usb://Canon/MF4100%20Series%20(FAX)"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[24]="PRINTER_INFO=Canon MF4100 Series"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[25]="PRINTER_LOCATION=hyerk-ubuntu"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[26]="PRINTER=Canon-MF4100-Series"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[27]="CUPS_FILETYPE=document"
D [14/May/2010:01:53:19 -0400] [Job 58] envp[28]="FINAL_CONTENT_TYPE=printer/Canon-MF4100-Series"
I [14/May/2010:01:53:19 -0400] [Job 58] Started filter /usr/lib/cups/filter/pstopdf (PID 3790)
I [14/May/2010:01:53:19 -0400] [Job 58] Started filter /usr/lib/cups/filter/pdftopdf (PID 3791)
I [14/May/2010:01:53:19 -0400] [Job 58] Started filter /usr/lib/cups/filter/cpdftocps (PID 3792)
I [14/May/2010:01:53:19 -0400] [Job 58] Started filter /usr/lib/cups/filter/pstoufr2cpca (PID 3793)
I [14/May/2010:01:53:19 -0400] [Job 58] Started backend /usr/lib/cups/backend/usb (PID 3795)
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon-MF4100-Series) from localhost
D [14/May/2010:01:53:19 -0400] [Job 58] pstopdf 6 args: 58 ken Test Page 1 PageSize=Letter job-uuid=urn:uuid:41b6a095-8c05-3c0b-5dc7-378dec893a8b job-originating-host-name=localhost /var/spool/cups/d00058-001
D [14/May/2010:01:53:19 -0400] [Job 58] PPD: /etc/cups/ppd/Canon-MF4100-Series.ppd
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] [Job 58] STATE: +connecting-to-device
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] [Job 58] pstoufr2cpca start.
D [14/May/2010:01:53:19 -0400] [Job 58] Resolution: 600
D [14/May/2010:01:53:19 -0400] [Job 58] pdftops argv[5] = 58 ken Test Page 1 PageSize=Letter job-uuid=urn:uuid:41b6a095-8c05-3c0b-5dc7-378dec893a8b job-originating-host-name=localhost
D [14/May/2010:01:53:19 -0400] [Job 58] PPD: /etc/cups/ppd/Canon-MF4100-Series.ppd
D [14/May/2010:01:53:19 -0400] [Job 58] /usr/bin/pdftops supports '-origpagesizes': yes
D [14/May/2010:01:53:19 -0400] [Job 58] PostScript Level: 2
D [14/May/2010:01:53:19 -0400] [Job 58] Duplex: no
D [14/May/2010:01:53:19 -0400] [Job 58] Resolution: 600
D [14/May/2010:01:53:19 -0400] [Job 58] Page size: Letter
D [14/May/2010:01:53:19 -0400] [Job 58] Page size: Letter
D [14/May/2010:01:53:19 -0400] [Job 58] Width: 612, height: 792, absolute margins: 14.173, 17.008, 597.827, 774.992
D [14/May/2010:01:53:19 -0400] [Job 58] Printer using device file "/dev/usblp1"...
D [14/May/2010:01:53:19 -0400] [Job 58] STATE: -connecting-to-device
D [14/May/2010:01:53:19 -0400] [Job 58] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x7f03f3e03670)
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] [Job 58] Width: 612, height: 792, absolute margins: 14.173, 17.008, 597.827, 774.992
D [14/May/2010:01:53:19 -0400] [Job 58] Relative margins: 14.173, 17.008, 14.173, 17.008
D [14/May/2010:01:53:19 -0400] [Job 58] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [14/May/2010:01:53:19 -0400] [Job 58] PostScript to be injected: 
D [14/May/2010:01:53:19 -0400] [Job 58] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [14/May/2010:01:53:19 -0400] [Job 58] Relative margins: 14.173, 17.008, 14.173, 17.008
D [14/May/2010:01:53:19 -0400] [Job 58] PPD options: -level2 -origpagesizes
D [14/May/2010:01:53:19 -0400] [Job 58] PostScript to be injected: 
D [14/May/2010:01:53:19 -0400] [Job 58] GPL Ghostscript 8.70: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 1.1 Get-Jobs 1
D [14/May/2010:01:53:19 -0400] Get-Jobs ipp://localhost/printers/
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [14/May/2010:01:53:19 -0400] cupsdCloseClient: 19
D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1
D [14/May/2010:01:53:19 -0400] Get-Notifications /
D [14/May/2010:01:53:19 -0400] cupsdIsAuthorized: requesting-user-name="ken"
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [14/May/2010:01:53:19 -0400] Get-Job-Attributes ipp://localhost/jobs/58
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/58) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1
D [14/May/2010:01:53:19 -0400] Get-Notifications /
D [14/May/2010:01:53:19 -0400] cupsdIsAuthorized: requesting-user-name="ken"
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [14/May/2010:01:53:19 -0400] cupsdCloseClient: 19
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [14/May/2010:01:53:19 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-MF4100-Series
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-MF4100-Series) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [14/May/2010:01:53:19 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-MF4100-Series
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-MF4100-Series) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [14/May/2010:01:53:19 -0400] cupsdCloseClient: 14
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [14/May/2010:01:53:19 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-MF4100-Series
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-MF4100-Series) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 20 WAITING Closing on EOF
D [14/May/2010:01:53:19 -0400] cupsdCloseClient: 20
D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1
D [14/May/2010:01:53:19 -0400] Get-Notifications /
D [14/May/2010:01:53:19 -0400] cupsdIsAuthorized: requesting-user-name="ken"
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 1.1 Get-Job-Attributes 1
D [14/May/2010:01:53:19 -0400] Get-Job-Attributes ipp://localhost/jobs/58
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/58) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [14/May/2010:01:53:19 -0400] cupsdCloseClient: 14
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] PID 3790 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [14/May/2010:01:53:19 -0400] PID 3791 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Printers
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Classes
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Default
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Printers
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Classes
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Default
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] [Job 58] Device copies: 1; device collate: 
D [14/May/2010:01:53:19 -0400] [Job 58] Running /usr/bin/pdftops  -level2 -origpagesizes /tmp/pdftops.AB2ii0 -
D [14/May/2010:01:53:19 -0400] [Job 58] Running pstops '58' 'ken' 'Test Page' '1' ' PageSize=Letter job-uuid=urn:uuid:41b6a095-8c05-3c0b-5dc7-378dec893a8b job-originating-host-name=localhost'
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Printers
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Classes
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [14/May/2010:01:53:19 -0400] CUPS-Get-Default
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [14/May/2010:01:53:19 -0400] [Job 58] Page = 612x792; 14,17 to 598,775
D [14/May/2010:01:53:19 -0400] [Job 58] slow_collate=0, slow_duplex=0, slow_order=0
D [14/May/2010:01:53:19 -0400] [Job 58] Before copy_comments - %!PS-Adobe-3.0
D [14/May/2010:01:53:19 -0400] [Job 58] %!PS-Adobe-3.0
D [14/May/2010:01:53:19 -0400] [Job 58] %%LanguageLevel: 2
D [14/May/2010:01:53:19 -0400] [Job 58] %%DocumentSuppliedResources: (atend)
D [14/May/2010:01:53:19 -0400] [Job 58] %%DocumentMedia: plain 612 792 0 () ()
D [14/May/2010:01:53:19 -0400] [Job 58] %%BoundingBox: 0 0 612 792
D [14/May/2010:01:53:19 -0400] [Job 58] %%Pages: 1
D [14/May/2010:01:53:19 -0400] [Job 58] %%EndComments
D [14/May/2010:01:53:19 -0400] [Job 58] Before copy_prolog - %%BeginDefaults
D [14/May/2010:01:53:19 -0400] [Job 58] Before copy_setup - %%BeginSetup
D [14/May/2010:01:53:19 -0400] [Job 58] Before page loop - %%Page: 1 1
D [14/May/2010:01:53:19 -0400] [Job 58] Copying page 1...
D [14/May/2010:01:53:19 -0400] [Job 58] pagew = 583.7, pagel = 758.0
D [14/May/2010:01:53:19 -0400] [Job 58] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [14/May/2010:01:53:19 -0400] [Job 58] PageLeft = 14.2, PageRight = 597.8
D [14/May/2010:01:53:19 -0400] [Job 58] PageTop = 775.0, PageBottom = 17.0
D [14/May/2010:01:53:19 -0400] [Job 58] PageWidth = 612.0, PageLength = 792.0
D [14/May/2010:01:53:19 -0400] [Job 58] Wrote 1 pages...
D [14/May/2010:01:53:19 -0400] PID 3792 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [14/May/2010:01:53:19 -0400] [Job 58] opvpOpenPrinter(463)
D [14/May/2010:01:53:19 -0400] [Job 58] Can't exec driver program
D [14/May/2010:01:53:19 -0400] [Job 58] Can't receive READY message
D [14/May/2010:01:53:19 -0400] [Job 58] Read 50 bytes of print data...
D [14/May/2010:01:53:19 -0400] [Job 58] STATE: -media-empty-warning
D [14/May/2010:01:53:19 -0400] [Job 58] STATE: -offline-report
I [14/May/2010:01:53:19 -0400] [Job 58] Printer is now online.
D [14/May/2010:01:53:19 -0400] [Job 58] Wrote 50 bytes of print data...
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] PID 3793 (/usr/lib/cups/filter/pstoufr2cpca) exited with no errors.
D [14/May/2010:01:53:19 -0400] PID 3795 (/usr/lib/cups/backend/usb) exited with no errors.
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
I [14/May/2010:01:53:19 -0400] [Job 58] Job completed.
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(----J-)
D [14/May/2010:01:53:19 -0400] cupsdMarkDirty(-----S)
D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 14 1.1 Get-Jobs 1
D [14/May/2010:01:53:19 -0400] Get-Jobs ipp://localhost/printers/
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:19 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [14/May/2010:01:53:19 -0400] Get-Notifications /
D [14/May/2010:01:53:19 -0400] cupsdIsAuthorized: requesting-user-name="ken"
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:19 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:19 -0400] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [14/May/2010:01:53:19 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-MF4100-Series
D [14/May/2010:01:53:19 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-MF4100-Series) from localhost
D [14/May/2010:01:53:19 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [14/May/2010:01:53:20 -0400] cupsdCloseClient: 14
D [14/May/2010:01:53:20 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [14/May/2010:01:53:20 -0400] [Job 58] Unloading...
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1
D [14/May/2010:01:53:20 -0400] Get-Notifications /
D [14/May/2010:01:53:20 -0400] cupsdIsAuthorized: requesting-user-name="ken"
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [14/May/2010:01:53:20 -0400] cupsdCloseClient: 14
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [14/May/2010:01:53:20 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-MF4100-Series
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-MF4100-Series) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [14/May/2010:01:53:20 -0400] cupsdCloseClient: 18
D [14/May/2010:01:53:20 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: No authentication data provided.
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1
D [14/May/2010:01:53:20 -0400] Get-Notifications /
D [14/May/2010:01:53:20 -0400] cupsdIsAuthorized: requesting-user-name="ken"
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [14/May/2010:01:53:20 -0400] cupsdCloseClient: 14
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [14/May/2010:01:53:20 -0400] CUPS-Get-Printers
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [14/May/2010:01:53:20 -0400] CUPS-Get-Classes
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [14/May/2010:01:53:20 -0400] CUPS-Get-Default
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [14/May/2010:01:53:20 -0400] CUPS-Get-Printers
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [14/May/2010:01:53:20 -0400] CUPS-Get-Classes
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/May/2010:01:53:20 -0400] cupsdAuthorize: Authorized as ken using PeerCred
D [14/May/2010:01:53:20 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [14/May/2010:01:53:20 -0400] CUPS-Get-Default
D [14/May/2010:01:53:20 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [14/May/2010:01:53:20 -0400] cupsdSetBusyState: Dirty files
I [14/May/2010:01:53:50 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [14/May/2010:01:53:50 -0400] Saving subscriptions.conf...
D [14/May/2010:01:53:50 -0400] cupsdSetBusyState: Not busy

```

Does anyone have any ideas on how I can get this thing to print? Thanks for any advice you have to offer.

---

### Post by devilized on 2010-05-15
bump - anyone?

---

### Post by bcharlessr on 2010-09-24
[http://support-in.canon-asia.com/contents/IN/EN/0100270807.html](http://support-in.canon-asia.com/contents/IN/EN/0100270807.html)

This link contains information and the download link to the recently updated cups driver(s). Here is their blurb:

Linux Printer Driver (UFR II) Ver.2.10E

Last Updated : 17-Aug-2010
Issue Number : 0100270807
OS
Linux
Detail

Thank you for using the Canon UFR II/UFR II LT Printer Driver for Linux. This UFR II/UFR II LT printer driver provides printing functions for Canon LBP printers operating under the CUPS (Common UNIX Printing System) environment, a printing system that operates on Linux operating systems.

When opened package it does contain 32 AND 64 bit drivers

---

### Post by orenyny on 2012-01-11
hello,

I have a similar issue.
It's a different model, but I did download the driver and went through all the frustrating work of installing the driver but the printer would still not print.

It says this:
"There is a missing print filter for printer 'Canon-D460-490'.

Anybody has an idea of what is this print filter that is missing and how to install it?

Thanks.

---


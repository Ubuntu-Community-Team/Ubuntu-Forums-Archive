---
title: "Dell A920 Error Log puzzle"
date: 2009-02-19
forum: Hardware
---

### Post by petersfreeman on 2009-02-19
I have installed the Lexmark Z600 driver for this printer as per numerous instructions in this forum.  When I try to print a test page I get this error log:

```
D [19/Feb/2009:00:07:40 -0800] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Feb/2009:00:07:40 -0800] cupsdReadClient: 13 POST /printers/DellAIO HTTP/1.1
D [19/Feb/2009:00:07:40 -0800] cupsdAuthorize: No authentication data provided.
D [19/Feb/2009:00:07:40 -0800] Print-Job ipp://localhost/printers/DellAIO
D [19/Feb/2009:00:07:40 -0800] add_job: requesting-user-name="peter"
D [19/Feb/2009:00:07:40 -0800] Adding default job-sheets values "none,none"...
I [19/Feb/2009:00:07:40 -0800] [Job 10] Adding start banner page "none".
I [19/Feb/2009:00:07:40 -0800] Saving subscriptions.conf...
I [19/Feb/2009:00:07:40 -0800] [Job 10] Adding end banner page "none".
I [19/Feb/2009:00:07:40 -0800] [Job 10] File of type application/postscript queued by "peter".
D [19/Feb/2009:00:07:40 -0800] [Job 10] hold_until=0
I [19/Feb/2009:00:07:40 -0800] [Job 10] Queued on "DellAIO" by "peter".
I [19/Feb/2009:00:07:40 -0800] Saving subscriptions.conf...
D [19/Feb/2009:00:07:40 -0800] [Job 10] job-sheets=none,none
D [19/Feb/2009:00:07:40 -0800] [Job 10] banner_page = 0
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[0]="DellAIO"
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[1]="10"
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[2]="peter"
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[3]="Test Page"
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[4]="1"
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[5]="job-uuid=urn:uuid:20e3de0b-a588-374d-703d-ea27d0793647"
D [19/Feb/2009:00:07:40 -0800] [Job 10] argv[6]="/var/spool/cups/d00010-001"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[9]="SERVER_ADMIN=root@Office"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[10]="SOFTWARE=CUPS/1.3.9"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[12]="TZ=America/Vancouver"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[13]="USER=root"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[16]="IPP_PORT=631"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[17]="CHARSET=utf-8"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[18]="LANG=en_CA.UTF8"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[19]="PPD=/etc/cups/ppd/DellAIO.ppd"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[20]="RIP_MAX_CACHE=8m"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[21]="CONTENT_TYPE=application/postscript"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[22]="DEVICE_URI=usb://Dell%20/A920"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[23]="PRINTER=DellAIO"
D [19/Feb/2009:00:07:40 -0800] [Job 10] envp[24]="FINAL_CONTENT_TYPE=printer/DellAIO"
I [19/Feb/2009:00:07:40 -0800] [Job 10] Started filter /usr/lib/cups/filter/pstopdf (PID 7741)
I [19/Feb/2009:00:07:40 -0800] [Job 10] Started filter /usr/lib/cups/filter/pdftopdf (PID 7742)
I [19/Feb/2009:00:07:40 -0800] [Job 10] Started filter /usr/lib/cups/filter/pdftoraster (PID 7743)
I [19/Feb/2009:00:07:40 -0800] [Job 10] Started filter /usr/lib/cups/filter/rastertoz600 (PID 7744)
I [19/Feb/2009:00:07:40 -0800] [Job 10] Started backend /usr/lib/cups/backend/usb (PID 7745)
I [19/Feb/2009:00:07:40 -0800] Saving subscriptions.conf...
D [19/Feb/2009:00:07:40 -0800] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
E [19/Feb/2009:00:07:40 -0800] PID 7744 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
D [19/Feb/2009:00:07:40 -0800] [Job 10] DellAIO: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
D [19/Feb/2009:00:07:40 -0800] [Job 10] pstopdf argv[6] = 10 peter Test Page 1 job-uuid=urn:uuid:20e3de0b-a588-374d-703d-ea27d0793647 /var/spool/cups/d00010-001
D [19/Feb/2009:00:07:40 -0800] [Job 10] PPD: /etc/cups/ppd/DellAIO.ppd
D [19/Feb/2009:00:07:40 -0800] [Job 10] Printer using device file "/dev/usblp0"...
D [19/Feb/2009:00:07:40 -0800] [Job 10] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb80e0a80)
I [19/Feb/2009:00:07:40 -0800] Saving subscriptions.conf...
D [19/Feb/2009:00:07:40 -0800] PID 7745 (/usr/lib/cups/backend/usb) exited with no errors.
D [19/Feb/2009:00:07:40 -0800] cupsdCloseClient: 13
D [19/Feb/2009:00:07:40 -0800] [Job 10] Resolution:
D [19/Feb/2009:00:07:40 -0800] [Job 10] Page size: Letter
D [19/Feb/2009:00:07:41 -0800] [Job 10] Width: 612, height: 792, absolute margins: , , ,
D [19/Feb/2009:00:07:41 -0800] [Job 10] Relative margins: 18, 36, 18, 5
D [19/Feb/2009:00:07:41 -0800] [Job 10] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [19/Feb/2009:00:07:41 -0800] [Job 10] PostScript to be injected:
D [19/Feb/2009:00:07:41 -0800] [Job 10] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [19/Feb/2009:00:07:41 -0800] [Job 10] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [19/Feb/2009:00:07:41 -0800] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Feb/2009:00:07:41 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Feb/2009:00:07:41 -0800] cupsdAuthorize: No authentication data provided.

```

Can anyone help me to get my printer working.

Thanks,

Peter

---

### Post by petersfreeman on 2009-02-19
What does it mean by:

> DellAIO: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Peter

---

### Post by petersfreeman on 2009-02-19
Has anyone actually got a Dell A920 to work?

---

### Post by petersfreeman on 2009-02-20
Is there a way in which I can test to see what is happening at each stage of the process so I can isolate the problem?

---


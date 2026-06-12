---
title: "HL2140 No network printing Ubuntu 12.10"
date: 2012-11-26
forum: Hardware
---

### Post by David_Melb on 2012-11-26
I Have installed Ubuntu 12.10 on a Samsung Laptopnp-r620h which is working fine.  Except I am unable to print via wireless or Ethernet to my printer HL2140 which is connected to a Telstra 3G21WB router.  It worked fine on 10.10 and 11.10 and the settings under properties is [http://router:631/printers/Brother](http://router:631/printers/Brother).
The printer works fine if connected to the USB port on the laptop.

The printer state IDLE - Filter Failed

The Error log attached


Does anyone have suggestions on how to fix the problem.  I did download and try the Brother Printer package to no Avail.:(

E [26/Nov/2012:16:58:47 +1100] [Job 39] Job stopped due to filter errors; please consult the error_log file for details.
D [26/Nov/2012:16:58:47 +1100] [Job 39] The following messages were recorded from 16:58:45 to 16:58:47
D [26/Nov/2012:16:58:47 +1100] [Job 39] Adding start banner page "none".
D [26/Nov/2012:16:58:47 +1100] [Job 39] Adding end banner page "none".
D [26/Nov/2012:16:58:47 +1100] [Job 39] File of type application/vnd.cups-pdf-banner queued by "david".
D [26/Nov/2012:16:58:47 +1100] [Job 39] hold_until=0
D [26/Nov/2012:16:58:47 +1100] [Job 39] Queued on "Brother-HL-2140" by "david".
D [26/Nov/2012:16:58:47 +1100] [Job 39] time-at-processing=1353909525
D [26/Nov/2012:16:58:47 +1100] [Job 39] job-sheets=none,none
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[0]="Brother-HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[1]="39"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[2]="david"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[3]="Test Page"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[4]="1"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[5]="job-uuid=urn:uuid:c855386b-4770-339f-4d8e-cd92063df2b5 job-originating-host-name=localhost time-at-creation=1353909525 time-at-processing=1353909525"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[6]="/var/spool/cups/d00039-001"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[8]="HOME=/var/spool/cups/tmp"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[10]="SERVER_ADMIN=root@Stewart-Samsung-Laptop"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[11]="SOFTWARE=CUPS/1.6.1"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[13]="USER=root"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[14]="CUPS_MAX_MESSAGE=2047"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[17]="IPP_PORT=631"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[18]="CHARSET=utf-8"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[19]="LANG=en_AU.UTF-8"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[20]="PPD=/etc/cups/ppd/Brother-HL-2140.ppd"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[21]="RIP_MAX_CACHE=128m"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[23]="DEVICE_URI=http://10.0.0.138:631/printers/Brother"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[24]="PRINTER_INFO=Brother HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[25]="PRINTER_LOCATION="
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[26]="PRINTER=Brother-HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[27]="PRINTER_STATE_REASONS=cups-ipp-conformance-failure-report,cups-ipp-missing-printer-is-accepting-jobs,cups-ipp-missing-printer-state-reasons,cups-ipp-missing-cancel-job,cups-ipp-missing-validate-job,cups-ipp-missing-job-id,shutdown"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[28]="CUPS_FILETYPE=document"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[29]="FINAL_CONTENT_TYPE=printer/Brother-HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[30]="AUTH_I****"
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started filter /usr/lib/cups/filter/bannertopdf (PID 3677)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started filter /usr/lib/cups/filter/pdftopdf (PID 3678)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started filter /usr/lib/cups/filter/foomatic-rip (PID 3679)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started backend /usr/lib/cups/backend/http (PID 3680)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Getting input from file 
D [26/Nov/2012:16:58:47 +1100] [Job 39] foomatic-rip version 4.0.17.256 running...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Parsing PPD file ...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option ColorSpace
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Resolution
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option PageSize
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option PrintoutMode
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option InputSlot
D [26/Nov/2012:16:58:47 +1100] [Job 39] Sending stdin for job...
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+connecting-to-device")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=1, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] STATE: +connecting-to-device
D [26/Nov/2012:16:58:47 +1100] [Job 39] Looking up "10.0.0.138"...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option ImageableArea
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3677 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option PaperDimension
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Duplex
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Quality
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Font
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3678 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Parameter Summary
D [26/Nov/2012:16:58:47 +1100] [Job 39] -----------------
D [26/Nov/2012:16:58:47 +1100] [Job 39] Spooler: cups
D [26/Nov/2012:16:58:47 +1100] [Job 39] Printer: Brother-HL-2140
D [26/Nov/2012:16:58:47 +1100] [Job 39] Shell: /bin/bash
D [26/Nov/2012:16:58:47 +1100] [Job 39] PPD file: /etc/cups/ppd/Brother-HL-2140.ppd
D [26/Nov/2012:16:58:47 +1100] [Job 39] ATTR file: 
D [26/Nov/2012:16:58:47 +1100] [Job 39] Printer model: Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Job title: Test Page
D [26/Nov/2012:16:58:47 +1100] [Job 39] File(s) to be printed:
D [26/Nov/2012:16:58:47 +1100] [Job 39] <STDIN>
D [26/Nov/2012:16:58:47 +1100] [Job 39] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [26/Nov/2012:16:58:47 +1100] [Job 39] Printing system options:
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'job-uuid=urn:uuid:c855386b-4770-339f-4d8e-cd92063df2b5'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option job-uuid=urn:uuid:c855386b-4770-339f-4d8e-cd92063df2b5.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'job-originating-host-name=localhost'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option job-originating-host-name=localhost.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'time-at-creation=1353909525'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option time-at-creation=1353909525.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'time-at-processing=1353909525'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option time-at-processing=1353909525.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Options from the PPD file:
D [26/Nov/2012:16:58:47 +1100] [Job 39] ================================================
D [26/Nov/2012:16:58:47 +1100] [Job 39] File: <STDIN>
D [26/Nov/2012:16:58:47 +1100] [Job 39] ================================================
D [26/Nov/2012:16:58:47 +1100] [Job 39] Filetype: PDF
D [26/Nov/2012:16:58:47 +1100] [Job 39] Storing temporary files in /var/spool/cups/tmp
D [26/Nov/2012:16:58:47 +1100] [Job 39] hrDeviceDesc="Unknown"
D [26/Nov/2012:16:58:47 +1100] [Job 39] prtGeneralCurrentLocalization type is 81, expected 2!
D [26/Nov/2012:16:58:47 +1100] [Job 39] backendWaitLoop(snmp_fd=6, addr=0xb9646e84, side_cb=0xb7755070)
D [26/Nov/2012:16:58:47 +1100] [Job 39] File contains 1 pages
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -dNOINTERPOLATE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-vA330b 
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting process "kid3" (generation 1)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting process "kid4" (generation 2)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting process "renderer" (generation 2)
D [26/Nov/2012:16:58:47 +1100] [Job 39] JCL: %-12345X@PJL
D [26/Nov/2012:16:58:47 +1100] [Job 39] <job data> 
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connecting to 10.0.0.138:631
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connecting to printer.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Set job-printer-state-message to "Connecting to printer.", current level=INFO
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="-cups-certificate-error")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='-', new_reasons=1, state_reasons=8
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="-connecting-to-device")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='-', new_reasons=1, state_reasons=8
D [26/Nov/2012:16:58:47 +1100] [Job 39] STATE: -connecting-to-device
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connected to printer.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Set job-printer-state-message to "Connected to printer.", current level=INFO
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connected to 10.0.0.138:631...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Getting supported attributes...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Get-Printer-Attributes: successful-ok (successful-ok)
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-printer-is-accepting-jobs")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] document-format-supported (1 values)
D [26/Nov/2012:16:58:47 +1100] [Job 39] [0] = "application/octet-stream"
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-cancel-job")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-validate-job")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=1(shutdown), s="(null)")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op=' ', new_reasons=1, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] final_content_type="printer/Brother-HL-2140", document_format="application/octet-stream"
D [26/Nov/2012:16:58:47 +1100] [Job 39] Print-Job IPP/2.0
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-uri="http://10.0.0.138:631/printers/Brother"
D [26/Nov/2012:16:58:47 +1100] [Job 39] requesting-user-name="david"
D [26/Nov/2012:16:58:47 +1100] [Job 39] job-name="39 - Test Page"
D [26/Nov/2012:16:58:47 +1100] [Job 39] document-format="application/octet-stream"
D [26/Nov/2012:16:58:47 +1100] [Job 39] Sending file using HTTP/1.1 chunking...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Print-Job: successful-ok (successful-ok)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Print file accepted - job ID unknown.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Set job-printer-state-message to "Print file accepted - job ID unknown.", current level=INFO
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-job-id")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] job-id=0
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=1(shutdown), s="(null)")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op=' ', new_reasons=1, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] Get-Printer-Attributes: successful-ok (successful-ok)
D [26/Nov/2012:16:58:47 +1100] [Job 39] ATTR: auth-info-required=none
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3680 (/usr/lib/cups/backend/http) exited with no errors.
D [26/Nov/2012:16:58:47 +1100] [Job 39] GPL Ghostscript 9.06: Unrecoverable error, exit code 1
D [26/Nov/2012:16:58:47 +1100] [Job 39] renderer exited with status 1
D [26/Nov/2012:16:58:47 +1100] [Job 39] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3679 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Hint: Try setting the LogLevel to "debug" to find out more.
D [26/Nov/2012:16:58:47 +1100] [Job 39] End of messages
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-state=3(idle)
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-state-message="Filter failed"
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-state-reasons=cups-ipp-conformance-failure-report,cups-ipp-missing-printer-is-accepting-jobs,cups-ipp-missing-printer-state-reasons,cups-ipp-missing-cancel-job,cups-ipp-missing-validate-job,cups-ipp-missing-job-id,shutdown

---

### Post by David_Melb on 2012-12-10
> **David_Melb said:**
> I Have installed Ubuntu 12.10 on a Samsung Laptopnp-r620h which is working fine.  Except I am unable to print via wireless or Ethernet to my printer HL2140 which is connected to a Telstra 3G21WB router.  It worked fine on 10.10 and 11.10 and the settings under properties is [http://router:631/printers/Brother](http://router:631/printers/Brother).
The printer works fine if connected to the USB port on the laptop.

The printer state IDLE - Filter Failed

The Error log attached


Does anyone have suggestions on how to fix the problem.  I did download and try the Brother Printer package to no Avail.:(

E [26/Nov/2012:16:58:47 +1100] [Job 39] Job stopped due to filter errors; please consult the error_log file for details.
D [26/Nov/2012:16:58:47 +1100] [Job 39] The following messages were recorded from 16:58:45 to 16:58:47
D [26/Nov/2012:16:58:47 +1100] [Job 39] Adding start banner page "none".
D [26/Nov/2012:16:58:47 +1100] [Job 39] Adding end banner page "none".
D [26/Nov/2012:16:58:47 +1100] [Job 39] File of type application/vnd.cups-pdf-banner queued by "david".
D [26/Nov/2012:16:58:47 +1100] [Job 39] hold_until=0
D [26/Nov/2012:16:58:47 +1100] [Job 39] Queued on "Brother-HL-2140" by "david".
D [26/Nov/2012:16:58:47 +1100] [Job 39] time-at-processing=1353909525
D [26/Nov/2012:16:58:47 +1100] [Job 39] job-sheets=none,none
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[0]="Brother-HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[1]="39"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[2]="david"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[3]="Test Page"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[4]="1"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[5]="job-uuid=urn:uuid:c855386b-4770-339f-4d8e-cd92063df2b5 job-originating-host-name=localhost time-at-creation=1353909525 time-at-processing=1353909525"
D [26/Nov/2012:16:58:47 +1100] [Job 39] argv[6]="/var/spool/cups/d00039-001"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[8]="HOME=/var/spool/cups/tmp"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[10]="SERVER_ADMIN=root@Stewart-Samsung-Laptop"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[11]="SOFTWARE=CUPS/1.6.1"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[13]="USER=root"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[14]="CUPS_MAX_MESSAGE=2047"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[17]="IPP_PORT=631"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[18]="CHARSET=utf-8"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[19]="LANG=en_AU.UTF-8"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[20]="PPD=/etc/cups/ppd/Brother-HL-2140.ppd"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[21]="RIP_MAX_CACHE=128m"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[23]="DEVICE_URI=http://10.0.0.138:631/printers/Brother"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[24]="PRINTER_INFO=Brother HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[25]="PRINTER_LOCATION="
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[26]="PRINTER=Brother-HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[27]="PRINTER_STATE_REASONS=cups-ipp-conformance-failure-report,cups-ipp-missing-printer-is-accepting-jobs,cups-ipp-missing-printer-state-reasons,cups-ipp-missing-cancel-job,cups-ipp-missing-validate-job,cups-ipp-missing-job-id,shutdown"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[28]="CUPS_FILETYPE=document"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[29]="FINAL_CONTENT_TYPE=printer/Brother-HL-2140"
D [26/Nov/2012:16:58:47 +1100] [Job 39] envp[30]="AUTH_I****"
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started filter /usr/lib/cups/filter/bannertopdf (PID 3677)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started filter /usr/lib/cups/filter/pdftopdf (PID 3678)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started filter /usr/lib/cups/filter/foomatic-rip (PID 3679)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Started backend /usr/lib/cups/backend/http (PID 3680)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Getting input from file 
D [26/Nov/2012:16:58:47 +1100] [Job 39] foomatic-rip version 4.0.17.256 running...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Parsing PPD file ...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option ColorSpace
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Resolution
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option PageSize
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option PrintoutMode
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option InputSlot
D [26/Nov/2012:16:58:47 +1100] [Job 39] Sending stdin for job...
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+connecting-to-device")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=1, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] STATE: +connecting-to-device
D [26/Nov/2012:16:58:47 +1100] [Job 39] Looking up "10.0.0.138"...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option ImageableArea
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3677 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option PaperDimension
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Duplex
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Quality
D [26/Nov/2012:16:58:47 +1100] [Job 39] Added option Font
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3678 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Parameter Summary
D [26/Nov/2012:16:58:47 +1100] [Job 39] -----------------
D [26/Nov/2012:16:58:47 +1100] [Job 39] Spooler: cups
D [26/Nov/2012:16:58:47 +1100] [Job 39] Printer: Brother-HL-2140
D [26/Nov/2012:16:58:47 +1100] [Job 39] Shell: /bin/bash
D [26/Nov/2012:16:58:47 +1100] [Job 39] PPD file: /etc/cups/ppd/Brother-HL-2140.ppd
D [26/Nov/2012:16:58:47 +1100] [Job 39] ATTR file: 
D [26/Nov/2012:16:58:47 +1100] [Job 39] Printer model: Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Job title: Test Page
D [26/Nov/2012:16:58:47 +1100] [Job 39] File(s) to be printed:
D [26/Nov/2012:16:58:47 +1100] [Job 39] <STDIN>
D [26/Nov/2012:16:58:47 +1100] [Job 39] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [26/Nov/2012:16:58:47 +1100] [Job 39] Printing system options:
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'job-uuid=urn:uuid:c855386b-4770-339f-4d8e-cd92063df2b5'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option job-uuid=urn:uuid:c855386b-4770-339f-4d8e-cd92063df2b5.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'job-originating-host-name=localhost'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option job-originating-host-name=localhost.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'time-at-creation=1353909525'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option time-at-creation=1353909525.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Pondering option 'time-at-processing=1353909525'
D [26/Nov/2012:16:58:47 +1100] [Job 39] Unknown option time-at-processing=1353909525.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Options from the PPD file:
D [26/Nov/2012:16:58:47 +1100] [Job 39] ================================================
D [26/Nov/2012:16:58:47 +1100] [Job 39] File: <STDIN>
D [26/Nov/2012:16:58:47 +1100] [Job 39] ================================================
D [26/Nov/2012:16:58:47 +1100] [Job 39] Filetype: PDF
D [26/Nov/2012:16:58:47 +1100] [Job 39] Storing temporary files in /var/spool/cups/tmp
D [26/Nov/2012:16:58:47 +1100] [Job 39] hrDeviceDesc="Unknown"
D [26/Nov/2012:16:58:47 +1100] [Job 39] prtGeneralCurrentLocalization type is 81, expected 2!
D [26/Nov/2012:16:58:47 +1100] [Job 39] backendWaitLoop(snmp_fd=6, addr=0xb9646e84, side_cb=0xb7755070)
D [26/Nov/2012:16:58:47 +1100] [Job 39] File contains 1 pages
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -dNOINTERPOLATE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-vA330b 
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting process "kid3" (generation 1)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting process "kid4" (generation 2)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Starting process "renderer" (generation 2)
D [26/Nov/2012:16:58:47 +1100] [Job 39] JCL: %-12345X@PJL
D [26/Nov/2012:16:58:47 +1100] [Job 39] <job data> 
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connecting to 10.0.0.138:631
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connecting to printer.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Set job-printer-state-message to "Connecting to printer.", current level=INFO
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="-cups-certificate-error")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='-', new_reasons=1, state_reasons=8
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="-connecting-to-device")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='-', new_reasons=1, state_reasons=8
D [26/Nov/2012:16:58:47 +1100] [Job 39] STATE: -connecting-to-device
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connected to printer.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Set job-printer-state-message to "Connected to printer.", current level=INFO
D [26/Nov/2012:16:58:47 +1100] [Job 39] Connected to 10.0.0.138:631...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Getting supported attributes...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Get-Printer-Attributes: successful-ok (successful-ok)
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-printer-is-accepting-jobs")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] document-format-supported (1 values)
D [26/Nov/2012:16:58:47 +1100] [Job 39] [0] = "application/octet-stream"
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-cancel-job")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-validate-job")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=1(shutdown), s="(null)")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op=' ', new_reasons=1, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] final_content_type="printer/Brother-HL-2140", document_format="application/octet-stream"
D [26/Nov/2012:16:58:47 +1100] [Job 39] Print-Job IPP/2.0
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-uri="http://10.0.0.138:631/printers/Brother"
D [26/Nov/2012:16:58:47 +1100] [Job 39] requesting-user-name="david"
D [26/Nov/2012:16:58:47 +1100] [Job 39] job-name="39 - Test Page"
D [26/Nov/2012:16:58:47 +1100] [Job 39] document-format="application/octet-stream"
D [26/Nov/2012:16:58:47 +1100] [Job 39] Sending file using HTTP/1.1 chunking...
D [26/Nov/2012:16:58:47 +1100] [Job 39] Print-Job: successful-ok (successful-ok)
D [26/Nov/2012:16:58:47 +1100] [Job 39] Print file accepted - job ID unknown.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Set job-printer-state-message to "Print file accepted - job ID unknown.", current level=INFO
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-missing-job-id")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op='+', new_reasons=2, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] job-id=0
D [26/Nov/2012:16:58:47 +1100] [Job 39] update_reasons(attr=1(shutdown), s="(null)")
D [26/Nov/2012:16:58:47 +1100] [Job 39] op=' ', new_reasons=1, state_reasons=7
D [26/Nov/2012:16:58:47 +1100] [Job 39] Get-Printer-Attributes: successful-ok (successful-ok)
D [26/Nov/2012:16:58:47 +1100] [Job 39] ATTR: auth-info-required=none
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3680 (/usr/lib/cups/backend/http) exited with no errors.
D [26/Nov/2012:16:58:47 +1100] [Job 39] GPL Ghostscript 9.06: Unrecoverable error, exit code 1
D [26/Nov/2012:16:58:47 +1100] [Job 39] renderer exited with status 1
D [26/Nov/2012:16:58:47 +1100] [Job 39] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [26/Nov/2012:16:58:47 +1100] [Job 39] PID 3679 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9.
D [26/Nov/2012:16:58:47 +1100] [Job 39] Hint: Try setting the LogLevel to "debug" to find out more.
D [26/Nov/2012:16:58:47 +1100] [Job 39] End of messages
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-state=3(idle)
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-state-message="Filter failed"
D [26/Nov/2012:16:58:47 +1100] [Job 39] printer-state-reasons=cups-ipp-conformance-failure-report,cups-ipp-missing-printer-is-accepting-jobs,cups-ipp-missing-printer-state-reasons,cups-ipp-missing-cancel-job,cups-ipp-missing-validate-job,cups-ipp-missing-job-id,shutdown
Has anyone have any sugestions on fixing this problem.

---


---
title: "Printer will only print test page"
date: 2015-11-03
forum: Hardware
---

### Post by kneebreeated on 2015-11-03
Whenever I try to print anything other than a test page the print job simply gets stopped. Here's my error log, tell me if you need anything else.


```


I [03/Nov/2015:16:52:00 -0500] [Job 93] Adding start banner page "none".D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [03/Nov/2015:16:52:00 -0500] [Job 93] Adding end banner page "none".
I [03/Nov/2015:16:52:00 -0500] [Job 93] File of type application/pdf queued by "sol".
D [03/Nov/2015:16:52:00 -0500] [Job 93] hold_until=0
I [03/Nov/2015:16:52:00 -0500] [Job 93] Queued on "HEWLETT-PACKARD-DESKJET-825C" by "sol".
D [03/Nov/2015:16:52:00 -0500] [Job 93] time-at-processing=1446587520
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:00 -0500] [Job 93] 3 filters for job:
D [03/Nov/2015:16:52:00 -0500] [Job 93] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [03/Nov/2015:16:52:00 -0500] [Job 93] gstoraster (application/vnd.cups-pdf to application/vnd.cups-raster, cost 99)
D [03/Nov/2015:16:52:00 -0500] [Job 93] hpcups (application/vnd.cups-raster to printer/HEWLETT-PACKARD-DESKJET-825C, cost 0)
D [03/Nov/2015:16:52:00 -0500] [Job 93] job-sheets=none,none
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[0]="HEWLETT-PACKARD-DESKJET-825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[1]="93"
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[2]="sol"
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[3]="coupon.pdf"
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[4]="1"
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[5]="InputSlot=Auto number-up=1 PageSize=Letter MediaType=Plain OutputMode=NormalGray job-uuid=urn:uuid:56c70def-57ff-3496-6eb9-1049d8e2ea66 job-originating-host-name=localhost time-at-creation=1446587520 time-at-processing=1446587520"
D [03/Nov/2015:16:52:00 -0500] [Job 93] argv[6]="/var/spool/cups/d00093-001"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[10]="SERVER_ADMIN=root@abacus"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[11]="SOFTWARE=CUPS/1.7.5"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[13]="USER=root"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[14]="CUPS_MAX_MESSAGE=2047"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[17]="IPP_PORT=631"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[18]="CHARSET=utf-8"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[19]="LANG=en_US.UTF-8"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[20]="PPD=/etc/cups/ppd/HEWLETT-PACKARD-DESKJET-825C.ppd"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[21]="RIP_MAX_CACHE=128m"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[22]="CONTENT_TYPE=application/pdf"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[23]="DEVICE_URI=usb://HP/DESKJET%20825C?serial=TH23M240H43H"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[24]="PRINTER_INFO=HEWLETT-PACKARD DESKJET 825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[25]="PRINTER_LOCATION=abacus"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[26]="PRINTER=HEWLETT-PACKARD-DESKJET-825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[27]="PRINTER_STATE_REASONS=none"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[28]="CUPS_FILETYPE=document"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[29]="FINAL_CONTENT_TYPE=printer/HEWLETT-PACKARD-DESKJET-825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[30]="AUTH_I****"
I [03/Nov/2015:16:52:00 -0500] [Job 93] Started filter /usr/lib/cups/filter/pdftopdf (PID 3003)
I [03/Nov/2015:16:52:00 -0500] [Job 93] Started filter /usr/lib/cups/filter/gstoraster (PID 3004)
I [03/Nov/2015:16:52:00 -0500] [Job 93] Started filter /usr/lib/cups/filter/hpcups (PID 3005)
I [03/Nov/2015:16:52:00 -0500] [Job 93] Started backend /usr/lib/cups/backend/usb (PID 3006)
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:00 -0500] [Client 21] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:00 -0500] [Client 21] Content-Length: 174
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=174, response=0xb91e0330(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:00 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:00 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:00 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:00 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Loading USB quirks from "/usr/share/cups/usb".
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Loaded 112 quirks.
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Printing on printer with URI: usb://HP/DESKJET%20825C?serial=TH23M240H43H
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] libusb_get_device_list=5
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] STATE: +connecting-to-device
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] STATE: -connecting-to-device
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Device protocol: 2
I [03/Nov/2015:16:52:00 -0500] [Job 93] Sending data to printer.
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] [Job 93] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Color Manager: Calibration Mode/Off
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] PID 3003 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Calling FindDeviceById(cups-HEWLETT-PACKARD-DESKJET-825C)
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Found device /org/freedesktop/ColorManager/devices/cups_HEWLETT_PACKARD_DESKJET_825C
D [03/Nov/2015:16:52:00 -0500] [Job 93] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Calling FindDeviceById(cups-HEWLETT-PACKARD-DESKJET-825C)
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Found device /org/freedesktop/ColorManager/devices/cups_HEWLETT_PACKARD_DESKJET_825C
D [03/Nov/2015:16:52:00 -0500] [Job 93] Calling GetProfileForQualifiers(RGB.Plain....)
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Found profile /org/freedesktop/ColorManager/profiles/HEWLETT_PACKARD_DESKJET_825C_RGB__
D [03/Nov/2015:16:52:00 -0500] [Job 93] Calling org.freedesktop.ColorManager.Profile.Get(Filename)
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Job 93] Use profile filename: ''
D [03/Nov/2015:16:52:00 -0500] [Job 93] Color Manager: ICC Profile: 
D [03/Nov/2015:16:52:00 -0500] [Job 93] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sMediaType=Plain -sOutputType=0 -r600x600 -dMediaPosition=7 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsRowStep=2 -dcupsInteger0=2 -scupsString0=PlainNormalGrayK -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c '<</.HWMargins[18.000000 36.000000 18.000000 9.000000] /Margins[0 0]>>setpagedevice' -f -_
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[10]="SERVER_ADMIN=root@abacus"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[11]="SOFTWARE=CUPS/1.7.5"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[12]="USER=root"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[13]="CUPS_MAX_MESSAGE=2047"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[16]="IPP_PORT=631"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[17]="CHARSET=utf-8"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[18]="LANG=en_US.UTF-8"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[19]="PPD=/etc/cups/ppd/HEWLETT-PACKARD-DESKJET-825C.ppd"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[20]="RIP_MAX_CACHE=128m"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[21]="CONTENT_TYPE=application/pdf"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[22]="DEVICE_URI=usb://HP/DESKJET%20825C?serial=TH23M240H43H"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[23]="PRINTER_INFO=HEWLETT-PACKARD DESKJET 825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[24]="PRINTER_LOCATION=abacus"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[25]="PRINTER=HEWLETT-PACKARD-DESKJET-825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[26]="PRINTER_STATE_REASONS=none"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[27]="CUPS_FILETYPE=document"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[28]="FINAL_CONTENT_TYPE=printer/HEWLETT-PACKARD-DESKJET-825C"
D [03/Nov/2015:16:52:00 -0500] [Job 93] envp[29]="AUTH_INFO_REQUIRED=none"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:00 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:00 -0500] [Client 21] 2.0 Get-Notifications 600
D [03/Nov/2015:16:52:00 -0500] Get-Notifications /
D [03/Nov/2015:16:52:00 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:00 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:00 -0500] [Client 21] Content-Length: 2009
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=2009, response=0xb9191600(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:00 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:00 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:00 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:00 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:00 -0500] [Client 18] 2.0 Get-Printer-Attributes 601
D [03/Nov/2015:16:52:00 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:00 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:00 -0500] [Client 18] Content-Length: 9721
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:00 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9721, response=0xb927e710(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:00 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:00 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:00 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:00 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:00 -0500] cupsd is not idle any more, canceling shutdown.
I [03/Nov/2015:16:52:01 -0500] [Job 93] Start rendering...
D [03/Nov/2015:16:52:01 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Job 93] Set job-printer-state-message to "Start rendering...", current level=INFO
D [03/Nov/2015:16:52:01 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
I [03/Nov/2015:16:52:01 -0500] [Job 93] Processing page 1...
D [03/Nov/2015:16:52:01 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Job 93] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [03/Nov/2015:16:52:01 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 18] 2.0 Get-Printer-Attributes 602
D [03/Nov/2015:16:52:01 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:01 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 18] Content-Length: 9717
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] 2.0 Get-Printer-Attributes 603
D [03/Nov/2015:16:52:01 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:01 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 18] Content-Length: 9717
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb91de008(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] 2.0 Get-Printer-Attributes 604
D [03/Nov/2015:16:52:01 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:01 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 18] Content-Length: 9717
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb9285cc0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 21] 2.0 Get-Notifications 605
D [03/Nov/2015:16:52:01 -0500] Get-Notifications /
D [03/Nov/2015:16:52:01 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:01 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 21] Content-Length: 5681
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=5681, response=0xb91be0b8(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 21] 2.0 Get-Job-Attributes 606
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 21] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 21] Content-Length: 942
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=942, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 607
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 608
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 609
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 610
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 611
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 612
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 21] 2.0 Get-Notifications 613
D [03/Nov/2015:16:52:01 -0500] Get-Notifications /
D [03/Nov/2015:16:52:01 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:01 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 21] Content-Length: 5681
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=5681, response=0xb91be0b8(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 21] 2.0 Get-Job-Attributes 614
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 21] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 21] Content-Length: 942
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=942, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Printer-Attributes 615
D [03/Nov/2015:16:52:01 -0500] Get-Printer-Attributes 
D [03/Nov/2015:16:52:01 -0500] Get-Printer-Attributes client-error-not-found: The printer or class does not exist.
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 130
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=130, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 616
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 101
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 617
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 101
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 618
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 101
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 619
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 101
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:01 -0500] [Client 24] 2.0 Get-Job-Attributes 620
D [03/Nov/2015:16:52:01 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:01 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:01 -0500] [Client 24] Content-Length: 101
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:01 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:01 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:01 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:01 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:01 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:01 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:02 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:02 -0500] [Client 14] 2.0 CUPS-Get-Printers 621
D [03/Nov/2015:16:52:02 -0500] CUPS-Get-Printers
D [03/Nov/2015:16:52:02 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 14] Content-Length: 533
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=533, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:02 -0500] [Client 14] 2.0 CUPS-Get-Classes 622
D [03/Nov/2015:16:52:02 -0500] CUPS-Get-Classes
D [03/Nov/2015:16:52:02 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 14] Content-Length: 75
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:02 -0500] [Client 14] 2.0 CUPS-Get-Default 623
D [03/Nov/2015:16:52:02 -0500] CUPS-Get-Default
D [03/Nov/2015:16:52:02 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 14] Content-Length: 9717
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:02 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:02 -0500] [Client 21] 2.0 Get-Notifications 624
D [03/Nov/2015:16:52:02 -0500] Get-Notifications /
D [03/Nov/2015:16:52:02 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:02 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 21] Content-Length: 1053
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=1053, response=0xb9286ce0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:02 -0500] [Client 18] 2.0 Get-Printer-Attributes 625
D [03/Nov/2015:16:52:02 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:02 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 18] Content-Length: 9717
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:02 -0500] [Client 18] 2.0 Get-Printer-Attributes 626
D [03/Nov/2015:16:52:02 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:02 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 18] Content-Length: 9717
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb91bf580(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:02 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:02 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:02 -0500] [Client 21] 2.0 Get-Notifications 627
D [03/Nov/2015:16:52:02 -0500] Get-Notifications /
D [03/Nov/2015:16:52:02 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:02 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 21] Content-Length: 127
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=127, response=0xb9286ce0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:02 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:02 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:0 2 -0500] [Client 21] 2.0 Get-Notifications 628
D [03/Nov/2015:16:52:02 -0500] Get-Notifications /
D [03/Nov/2015:16:52:02 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:02 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 21] Content-Length: 127
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=127, response=0xb9286ce0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:02 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:02 -0500] [Client 14] 2.0 CUPS-Get-Printers 629
D [03/Nov/2015:16:52:02 -0500] CUPS-Get-Printers
D [03/Nov/2015:16:52:02 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 14] Content-Length: 533
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=533, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:02 -0500] [Client 14] 2.0 CUPS-Get-Classes 630
D [03/Nov/2015:16:52:02 -0500] CUPS-Get-Classes
D [03/Nov/2015:16:52:02 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 14] Content-Length: 75
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:02 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:02 -0500] [Client 14] 2.0 CUPS-Get-Default 631
D [03/Nov/2015:16:52:02 -0500] CUPS-Get-Default
D [03/Nov/2015:16:52:02 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Nov/2015:16:52:02 -0500] [Client 14] Content-Length: 9717
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:02 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:02 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:02 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:02 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:02 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:03 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:04 -0500] [Job 93] Read 8192 bytes of print data...
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:04 -0500] [Job 93] prnt/hpcups/Pcl3Gui.cpp 75: Requested resolution not supported with requested printmodeprnt/hpcups/HPCupsFilter.cpp 456: m_Job initialization failed with error = 25
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:04 -0500] [Job 93] PID 3005 (/usr/lib/cups/filter/hpcups) stopped with status 1.
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:04 -0500] [Job 93] Wrote 8192 bytes of print data...
D [03/Nov/2015:16:52:04 -0500] [Job 93] Read 1858 bytes of print data...
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
I [03/Nov/2015:16:52:04 -0500] [Job 93] Processing page 2...
D [03/Nov/2015:16:52:04 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:04 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:04 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:04 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:04 -0500] [Job 93] Wrote 1858 bytes of print data...
D [03/Nov/2015:16:52:04 -0500] [Job 93] Sent 10050 bytes...
D [03/Nov/2015:16:52:04 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:05 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:05 -0500] [Client 21] 2.0 Get-Notifications 632
D [03/Nov/2015:16:52:05 -0500] Get-Notifications /
D [03/Nov/2015:16:52:05 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:05 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 21] Content-Length: 590
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=590, response=0xb9246fa0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:05 -0500] [Client 18] 2.0 Get-Printer-Attributes 633
D [03/Nov/2015:16:52:05 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:05 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 18] Content-Length: 9717
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb9280318(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:05 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:05 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:05 -0500] [Client 21] 2.0 Get-Notifications 634
D [03/Nov/2015:16:52:05 -0500] Get-Notifications /
D [03/Nov/2015:16:52:05 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:05 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 21] Content-Length: 1142
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=1142, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:05 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:05 -0500] [Client 24] 2.0 Get-Job-Attributes 635
D [03/Nov/2015:16:52:05 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:05 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 24] Content-Length: 75
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:05 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:05 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:05 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:05 -0500] [Client 21] 2.0 Get-Notifications 636
D [03/Nov/2015:16:52:05 -0500] Get-Notifications /
D [03/Nov/2015:16:52:05 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:05 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 21] Content-Length: 1142
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=1142, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:05 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:05 -0500] [Client 24] 2.0 Get-Job-Attributes 637
D [03/Nov/2015:16:52:05 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:05 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 24] Content-Length: 101
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 24] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:05 -0500] [Client 24] Closing connection.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:05 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:05 -0500] [Client 14] 2.0 CUPS-Get-Printers 638
D [03/Nov/2015:16:52:05 -0500] CUPS-Get-Printers
D [03/Nov/2015:16:52:05 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 14] Content-Length: 533
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=533, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:05 -0500] [Client 14] 2.0 CUPS-Get-Classes 639
D [03/Nov/2015:16:52:05 -0500] CUPS-Get-Classes
D [03/Nov/2015:16:52:05 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 14] Content-Length: 75
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:05 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:05 -0500] [Client 14] 2.0 CUPS-Get-Default 640
D [03/Nov/2015:16:52:05 -0500] CUPS-Get-Default
D [03/Nov/2015:16:52:05 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Nov/2015:16:52:05 -0500] [Client 14] Content-Length: 9717
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9717, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:05 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:05 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:05 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:05 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Job 93] Waiting for read thread to exit...
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:05 -0500] [Job 93] PID 3006 (/usr/lib/cups/backend/usb) exited with no errors.
D [03/Nov/2015:16:52:05 -0500] cupsd is not idle any more, canceling shutdown.
I [03/Nov/2015:16:52:06 -0500] [Job 93] Rendering completed
D [03/Nov/2015:16:52:06 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/No v/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Job 93] PID 3004 (/usr/lib/cups/filter/gstoraster) exited with no errors.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
E [03/Nov/2015:16:52:06 -0500] [Job 93] Job stopped due to filter errors; please consult the error_log file for details.
D [03/Nov/2015:16:52:06 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:06 -0500] [Job 93] The following messages were recorded from 16:52:00 to 16:52:00
D [03/Nov/2015:16:52:06 -0500] [Job 93] Printer found with device ID: MFG:HEWLETT-PACKARD;MDL:DESKJET 825C;CMD:MLC,PCL,PML;CLASS:PRINTER;DESCRIPTION:Hewlett-Packard DeskJet 825C;SERN:TH23M240H43H;VSTATUS:$HB0$AU0,ff,DN,IDLE,CUT;VP:0800,FL,B0; Device URI: usb://HP/DESKJET%20825C?serial=TH23M240H43H
D [03/Nov/2015:16:52:06 -0500] [Job 93] End of messages
D [03/Nov/2015:16:52:06 -0500] [Job 93] printer-state=3(idle)
D [03/Nov/2015:16:52:06 -0500] [Job 93] printer-state-message="Rendering completed"
D [03/Nov/2015:16:52:06 -0500] [Job 93] printer-state-reasons=none
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Printing jobs and dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] [Client 21] 2.0 Get-Notifications 641
D [03/Nov/2015:16:52:06 -0500] Get-Notifications /
D [03/Nov/2015:16:52:06 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:06 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 21] Content-Length: 1061
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=1061, response=0xb9191ec8(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 18] 2.0 Get-Printer-Attributes 642
D [03/Nov/2015:16:52:06 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:06 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 18] Content-Length: 9716
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9716, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 18] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 18] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 18] 2.0 Get-Printer-Attributes 643
D [03/Nov/2015:16:52:06 -0500] Get-Printer-Attributes ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:06 -0500] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 18] Content-Length: 9716
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 18] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9716, response=0xb9286248(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 18] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 18] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] 2.0 Get-Notifications 644
D [03/Nov/2015:16:52:06 -0500] Get-Notifications /
D [03/Nov/2015:16:52:06 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:06 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 21] Content-Length: 2228
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=2228, response=0xb921e380(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 22] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] 2.0 Get-Job-Attributes 645
D [03/Nov/2015:16:52:06 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:06 -0500] [Client 22] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 22] Content-Length: 75
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb927e698(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 22] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 22] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 22] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] [Client 22] 2.0 Get-Job-Attributes 646
D [03/Nov/2015:16:52:06 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:06 -0500] [Client 22] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 22] Content-Length: 75
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb9191418(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 22] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] 2.0 Get-Printer-Attributes 647
D [03/Nov/2015:16:52:06 -0500] Get-Printer-Attributes ipp://abacus/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:06 -0500] [Client 24] Returning IPP successful-ok for Get-Printer-Attributes (ipp://abacus/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 24] Content-Length: 134
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=134, response=0xb9191d10(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 24] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] 2.0 Get-Job-Attributes 648
D [03/Nov/2015:16:52:06 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:06 -0500] [Client 24] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 24] Content-Length: 120
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 24] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=120, response=0xb9191d68(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 24] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 24] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 24] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 22] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] 2.0 Get-Notifications 649
D [03/Nov/2015:16:52:06 -0500] Get-Notifications /
D [03/Nov/2015:16:52:06 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:06 -0500] [Client 21] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 21] Content-Length: 2228
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=2228, response=0xb9233040(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 22] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] 2.0 Get-Job-Attributes 650
D [03/Nov/2015:16:52:06 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:06 -0500] [Client 22] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 22] Content-Length: 101
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb9191d10(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 22] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 22] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 22] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] 2.0 Get-Job-Attributes 651
D [03/Nov/2015:16:52:06 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:06 -0500] [Client 22] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 22] Content-Length: 101
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=101, response=0xb923a238(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 22] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:06 -0500] [Client 25] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 25] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] 2.0 Get-Printer-Attributes 652
D [03/Nov/2015:16:52:06 -0500] Get-Printer-Attributes ipp://abacus/printers/HEWLETT-PACKARD-DESKJET-825C
D [03/Nov/2015:16:52:06 -0500] [Client 25] Returning IPP successful-ok for Get-Printer-Attributes (ipp://abacus/printers/HEWLETT-PACKARD-DESKJET-825C) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 25] Content-Length: 134
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=134, response=0xb92873d0(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 25] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 25] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 25] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 25] No authentication data provided.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] 2.0 Get-Job-Attributes 653
D [03/Nov/2015:16:52:06 -0500] Get-Job-Attributes ipp://localhost/jobs/93
D [03/Nov/2015:16:52:06 -0500] [Client 25] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 25] Content-Length: 120
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 25] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=120, response=0xb921e380(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 25] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 25] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 25] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 22] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 22] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:06 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] 2.0 CUPS-Get-Printers 654
D [03/Nov/2015:16:52:06 -0500] CUPS-Get-Printers
D [03/Nov/2015:16:52:06 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 14] Content-Length: 532
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=532, response=0xb9272650(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:06 -0500] [Client 14] 2.0 CUPS-Get-Classes 655
D [03/Nov/2015:16:52:06 -0500] CUPS-Get-Classes
D [03/Nov/2015:16:52:06 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 14] Content-Length: 75
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb91ca028(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] POST / HTTP/1.1
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:06 -0500] [Client 14] Authorized as sol using PeerCred
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] 2.0 CUPS-Get-Default 656
D [03/Nov/2015:16:52:06 -0500] CUPS-Get-Default
D [03/Nov/2015:16:52:06 -0500] [Client 14] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Nov/2015:16:52:06 -0500] [Client 14] Content-Length: 9716
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:06 -0500] [Client 14] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=9716, response=0xb9272650(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:06 -0500] [Client 14] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:06 -0500] [Client 14] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:06 -0500] [Client 14] Waiting for request.
D [03/Nov/2015:16:52:06 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:06 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:07 -0500] [Job 93] Unloading...
D [03/Nov/2015:16:52:07 -0500] cupsd is not idle any more, canceling shutdown.
I [03/Nov/2015:16:52:31 -0500] Saving job.cache...
I [03/Nov/2015:16:52:31 -0500] Saving subscriptions.conf...
D [03/Nov/2015:16:52:32 -0500] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
D [03/Nov/2015:16:52:32 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 21] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:33 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 21] POST /jobs/ HTTP/1.1
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [03/Nov/2015:16:52:33 -0500] [Client 21] No authentication data provided.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 21] 2.0 Cancel-Job 657
D [03/Nov/2015:16:52:33 -0500] Cancel-Job ipp://localhost/jobs/93
D [03/Nov/2015:16:52:33 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:33 -0500] [Job 93] Loading attributes...
D [03/Nov/2015:16:52:33 -0500] [Job 93] time-at-completed=1446587553
D [03/Nov/2015:16:52:33 -0500] cupsdMarkDirty(----S)
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"
I [03/Nov/2015:16:52:33 -0500] [Job 93] Job canceled by "sol"
D [03/Nov/2015:16:52:33 -0500] cupsdMarkDirty(---J-)
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [03/Nov/2015:16:52:33 -0500] [Job 93] Canceled by "sol".
D [03/Nov/2015:16:52:33 -0500] [Client 21] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/93) from localhost
D [03/Nov/2015:16:52:33 -0500] [Client 21] Content-Length: 75
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 21] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=75, response=0xb9228530(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:33 -0500] [Client 21] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:33 -0500] [Client 21] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:33 -0500] [Client 21] Waiting for request.
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 22] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:33 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 22] POST / HTTP/1.1
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:33 -0500] [Client 22] No authentication data provided.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 22] 2.0 Get-Notifications 658
D [03/Nov/2015:16:52:33 -0500] Get-Notifications /
D [03/Nov/2015:16:52:33 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:33 -0500] [Client 22] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:33 -0500] [Client 22] Content-Length: 689
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:33 -0500] [Client 22] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=689, response=0xb9233040(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:33 -0500] [Client 22] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:33 -0500] [Client 22] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:33 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:33 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:33 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] [Client 22] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:34 -0500] [Client 22] Closing connection.
D [03/Nov/2015:16:52:34 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] [Client 22] Accepted from localhost (Domain)
D [03/Nov/2015:16:52:34 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] [Client 22] POST / HTTP/1.1
D [03/Nov/2015:16:52:34 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:34 -0500] [Client 22] No authentication data provided.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] [Client 22] 2.0 Get-Notifications 659
D [03/Nov/2015:16:52:34 -0500] Get-Notifications /
D [03/Nov/2015:16:52:34 -0500] cupsdIsAuthorized: requesting-user-name="sol"
D [03/Nov/2015:16:52:34 -0500] [Client 22] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Nov/2015:16:52:34 -0500] [Client 22] Content-Length: 689
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] [Client 22] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=689, response=0xb9233098(IPP_IDLE), pipe_pid=0, file=-1
D [03/Nov/2015:16:52:34 -0500] [Client 22] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [03/Nov/2015:16:52:34 -0500] [Client 22] bytes=0, http_state=0, data_remaining=0
D [03/Nov/2015:16:52:34 -0500] [Client 22] Waiting for request.
D [03/Nov/2015:16:52:34 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:34 -0500] [Client 22] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:34 -0500] [Client 22] Closing connection.
D [03/Nov/2015:16:52:34 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:34 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:35 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:35 -0500] [Client 21] HTTP_STATE_WAITING Closing on EOF
D [03/Nov/2015:16:52:35 -0500] [Client 21] Closing connection.
D [03/Nov/2015:16:52:35 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:35 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:36 -0500] cupsd is not idle any more, canceling shutdown.
D [03/Nov/2015:16:52:55 -0500] [Job 92] Unloading...
D [03/Nov/2015:16:52:55 -0500] Closing client 19 after 300 seconds of inactivity...
D [03/Nov/2015:16:52:55 -0500] [Client 19] Closing connection.
D [03/Nov/2015:16:52:55 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [03/Nov/2015:16:52:55 -0500] Report: clients=9
D [03/Nov/2015:16:52:55 -0500] Report: jobs=8
D [03/Nov/2015:16:52:55 -0500] Report: jobs-active=0
D [03/Nov/2015:16:52:55 -0500] Report: printers=1
D [03/Nov/2015:16:52:55 -0500] Report: stringpool-string-count=13818
D [03/Nov/2015:16:52:55 -0500] Report: stringpool-alloc-bytes=15008
D [03/Nov/2015:16:52:55 -0500] Report: stringpool-total-bytes=290352
D [03/Nov/2015:16:52:55 -0500] cupsd is not idle any more, canceling shutdown.
I [03/Nov/2015:16:53:04 -0500] Saving job.cache...
I [03/Nov/2015:16:53:04 -0500] Saving subscriptions.conf...
D [03/Nov/2015:16:53:04 -0500] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
D [03/Nov/2015:16:53:04 -0500] cupsd is not idle any more, canceling shutdown.



```

---

### Post by tgalati4 on 2015-11-05
"Dirty" files implies communications error, which could be a cable or USB port issue.  Try a different USB cable and a different USB port.  Delete the printer and reinstall, then print one simple document, and post the error log.  There are 2 types of test pages, the HP test page and the Ubuntu/CUPS test page.  Which one prints out OK?

---


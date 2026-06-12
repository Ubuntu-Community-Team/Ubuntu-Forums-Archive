---
title: "/usr/lib/cups/filter/cpdftocps failed"
date: 2009-11-24
forum: Hardware
---

### Post by pdc on 2009-11-24
I think the problem stemmed from installing the adobe printing utility; 

after that, my CanonLBP3100 gives me the above error;

I note this problem reported before

[http://ubuntuforums.org/showthread.php?t=1121785](http://ubuntuforums.org/showthread.php?t=1121785)

and was solved by the person installing another distro; I would like to avoid that step if possible 

error message shows:

D [24/Nov/2009:19:22:22 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:22 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:22 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:22 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:22 +1300] Get-Jobs ipp://localhost/jobs/
D [24/Nov/2009:19:22:22 +1300] [Job 200] Loading attributes...
D [24/Nov/2009:19:22:22 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:22 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:22 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:22 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:22 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:22 +1300] Create-Printer-Subscription /
D [24/Nov/2009:19:22:22 +1300] cupsdCreateSubscription(con=0xb9679e98(11), uri="/")
D [24/Nov/2009:19:22:22 +1300] pullmethod="ippget"
D [24/Nov/2009:19:22:22 +1300] notify-lease-duration=86400
D [24/Nov/2009:19:22:22 +1300] notify-time-interval=0
D [24/Nov/2009:19:22:22 +1300] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [24/Nov/2009:19:22:22 +1300] Added subscription 92 for server
I [24/Nov/2009:19:22:22 +1300] Saving subscriptions.conf...
D [24/Nov/2009:19:22:22 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:22 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:23 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:23 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:23 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:23 +1300] Get-Notifications /
D [24/Nov/2009:19:22:23 +1300] cupsdIsAuthorized: requesting-user-name="pdc"
D [24/Nov/2009:19:22:23 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:23 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:34 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:34 +1300] cupsdReadClient: 11 POST /printers/LBP3100 HTTP/1.1
D [24/Nov/2009:19:22:34 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:34 +1300] Print-Job ipp://localhost/printers/LBP3100
D [24/Nov/2009:19:22:34 +1300] add_job: requesting-user-name="pdc"
D [24/Nov/2009:19:22:34 +1300] Adding default job-sheets values "none,none"...
I [24/Nov/2009:19:22:34 +1300] [Job 201] Adding start banner page "none".
I [24/Nov/2009:19:22:34 +1300] Saving subscriptions.conf...
I [24/Nov/2009:19:22:34 +1300] [Job 201] Adding end banner page "none".
I [24/Nov/2009:19:22:34 +1300] [Job 201] File of type application/postscript queued by "pdc".
D [24/Nov/2009:19:22:34 +1300] [Job 201] hold_until=0
I [24/Nov/2009:19:22:34 +1300] [Job 201] Queued on "LBP3100" by "pdc".
I [24/Nov/2009:19:22:34 +1300] Saving subscriptions.conf...
D [24/Nov/2009:19:22:34 +1300] [Job 201] job-sheets=none,none
D [24/Nov/2009:19:22:34 +1300] [Job 201] banner_page = 0
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[0]="LBP3100"
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[1]="201"
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[2]="pdc"
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[3]="Test Page"
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[4]="1"
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[5]="job-uuid=urn:uuid:d52ad653-e62d-309c-4910-7aa7fd197545"
D [24/Nov/2009:19:22:34 +1300] [Job 201] argv[6]="/var/spool/cups/d00201-001"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[9]="SERVER_ADMIN=root@pdc-desktop"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[10]="SOFTWARE=CUPS/1.3.9"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[12]="TZ=Pacific/Auckland"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[13]="USER=root"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[16]="IPP_PORT=631"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[17]="CHARSET=utf-8"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[18]="LANG=en_NZ.UTF8"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[19]="PPD=/etc/cups/ppd/LBP3100.ppd"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[20]="RIP_MAX_CACHE=8m"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[21]="CONTENT_TYPE=application/postscript"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[22]="DEVICE_URI=ccp:/var/ccpd/fifo0"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[23]="PRINTER=LBP3100"
D [24/Nov/2009:19:22:34 +1300] [Job 201] envp[24]="FINAL_CONTENT_TYPE=printer/LBP3100"
I [24/Nov/2009:19:22:34 +1300] [Job 201] Started filter /usr/lib/cups/filter/pstopdf (PID 10233)
I [24/Nov/2009:19:22:34 +1300] [Job 201] Started filter /usr/lib/cups/filter/pdftopdf (PID 10234)
I [24/Nov/2009:19:22:34 +1300] [Job 201] Started filter /usr/lib/cups/filter/cpdftocps (PID 10244)
I [24/Nov/2009:19:22:34 +1300] [Job 201] Started filter /usr/lib/cups/filter/pstocapt3 (PID 10245)
I [24/Nov/2009:19:22:34 +1300] [Job 201] Started backend /usr/lib/cups/backend/ccp (PID 10246)
I [24/Nov/2009:19:22:34 +1300] Saving subscriptions.conf...
D [24/Nov/2009:19:22:34 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:34 +1300] [Job 201] pstopdf argv[6] = 201 pdc Test Page 1 job-uuid=urn:uuid:d52ad653-e62d-309c-4910-7aa7fd197545 /var/spool/cups/d00201-001
D [24/Nov/2009:19:22:34 +1300] [Job 201] PPD: /etc/cups/ppd/LBP3100.ppd
D [24/Nov/2009:19:22:34 +1300] [Job 201] Resolution: 600
D [24/Nov/2009:19:22:34 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:34 +1300] [Job 201] pstocapt3 start.
D [24/Nov/2009:19:22:34 +1300] [Job 201] Page size: A4
D [24/Nov/2009:19:22:34 +1300] [Job 201] Width: , height: , absolute margins: , , ,
D [24/Nov/2009:19:22:34 +1300] [Job 201] Relative margins: , , ,
D [24/Nov/2009:19:22:34 +1300] [Job 201] PPD options: -r600
D [24/Nov/2009:19:22:34 +1300] [Job 201] PostScript to be injected:
D [24/Nov/2009:19:22:34 +1300] [Job 201] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/printer -r600 - -
D [24/Nov/2009:19:22:34 +1300] [Job 201] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [24/Nov/2009:19:22:34 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:34 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:34 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:34 +1300] Get-Notifications /
D [24/Nov/2009:19:22:34 +1300] cupsdIsAuthorized: requesting-user-name="pdc"
D [24/Nov/2009:19:22:34 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:34 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:34 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:34 +1300] Get-Job-Attributes ipp://localhost/jobs/201
D [24/Nov/2009:19:22:34 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:34 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:34 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:34 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:34 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:34 +1300] Get-Notifications /
D [24/Nov/2009:19:22:34 +1300] cupsdIsAuthorized: requesting-user-name="pdc"
D [24/Nov/2009:19:22:34 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:34 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:35 +1300] PID 10233 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [24/Nov/2009:19:22:35 +1300] PID 10234 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Nov/2009:19:22:35 +1300] [Job 201] Can't open /dev/null: Permission denied
E [24/Nov/2009:19:22:35 +1300] PID 10244 (/usr/lib/cups/filter/cpdftocps) stopped with status 13!
D [24/Nov/2009:19:22:35 +1300] cupsdReadClient: 7 POST / HTTP/1.1
D [24/Nov/2009:19:22:35 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:35 +1300] Get-Jobs ipp://localhost/printers/LBP3100
D [24/Nov/2009:19:22:35 +1300] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:35 +1300] [Job 201] ccp: last data.
D [24/Nov/2009:19:22:35 +1300] [Job 201] ccp: end of send data.
D [24/Nov/2009:19:22:35 +1300] PID 10246 (/usr/lib/cups/backend/ccp) exited with no errors.
D [24/Nov/2009:19:22:35 +1300] PID 10245 (/usr/lib/cups/filter/pstocapt3) exited with no errors.
D [24/Nov/2009:19:22:35 +1300] [Job 201] File 0 is complete.
E [24/Nov/2009:19:22:35 +1300] [Job 201] Job stopped due to filter errors.
I [24/Nov/2009:19:22:35 +1300] Saving subscriptions.conf...
I [24/Nov/2009:19:22:35 +1300] Saving subscriptions.conf...
D [24/Nov/2009:19:22:35 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:35 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:35 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:35 +1300] Get-Notifications /
D [24/Nov/2009:19:22:35 +1300] cupsdIsAuthorized: requesting-user-name="pdc"
D [24/Nov/2009:19:22:35 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:35 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:35 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:35 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:35 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:35 +1300] Get-Notifications /
D [24/Nov/2009:19:22:35 +1300] cupsdIsAuthorized: requesting-user-name="pdc"
D [24/Nov/2009:19:22:35 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:35 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:36 +1300] [Job 201] Unloading...
D [24/Nov/2009:19:22:48 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:48 +1300] Report: clients=3
D [24/Nov/2009:19:22:48 +1300] Report: jobs=200
D [24/Nov/2009:19:22:48 +1300] Report: jobs-active=3
D [24/Nov/2009:19:22:48 +1300] Report: printers=3
D [24/Nov/2009:19:22:48 +1300] Report: printers-implicit=0
D [24/Nov/2009:19:22:48 +1300] Report: stringpool-string-count=1366
D [24/Nov/2009:19:22:48 +1300] Report: stringpool-alloc-bytes=9800
D [24/Nov/2009:19:22:48 +1300] Report: stringpool-total-bytes=23880
D [24/Nov/2009:19:22:48 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:48 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:48 +1300] Get-Job-Attributes ipp://localhost/jobs/199
D [24/Nov/2009:19:22:48 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:48 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:48 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:48 +1300] Get-Job-Attributes ipp://localhost/jobs/201
D [24/Nov/2009:19:22:48 +1300] [Job 201] Loading attributes...
D [24/Nov/2009:19:22:48 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:48 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:48 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:48 +1300] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Nov/2009:19:22:48 +1300] cupsdAuthorize: No authentication data provided.
D [24/Nov/2009:19:22:48 +1300] Cancel-Subscription /
D [24/Nov/2009:19:22:48 +1300] cupsdIsAuthorized: requesting-user-name="pdc"
I [24/Nov/2009:19:22:48 +1300] Saving subscriptions.conf...
D [24/Nov/2009:19:22:48 +1300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Nov/2009:19:22:48 +1300] cupsdCloseClient: 11
D [24/Nov/2009:19:22:48 +1300] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Nov/2009:19:22:48 +1300] cupsdCloseClient: 10
D [24/Nov/2009:19:22:48 +1300] cupsdReadClient: 11 GET /admin/log/error_log

I have since deleted this adobe utility but the problem remains unchanged

---

### Post by linds2009 on 2009-11-24
code>Looks interesting i'll have to check it out.

---


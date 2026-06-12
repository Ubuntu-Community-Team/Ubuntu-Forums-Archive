---
title: "Printing halts immediatly."
date: 2012-08-14
forum: Hardware
---

### Post by ferulebezel on 2012-08-14
I just installed a HP p1102 at work.  Cups found it and it worked the first time and that's it.

Now whenever I try to print anything it is immediately halted in the que.  When I try to release it it again halts immediately.

Where can I find any error messages or better yet, What's wrong?

---

### Post by aikishugyo on 2012-08-15
In the CUPS web interface on [http://localhost:631](http://localhost:631) go to the Admin tab and then look at the log. You can enable debug messages and see more information after that.

Likely this is a problem with CUPS, not the driver for the printer.

---

### Post by ferulebezel on 2012-08-17
> **aikishugyo said:**
> In the CUPS web interface on [http://localhost:631](http://localhost:631) go to the Admin tab and then look at the log. You can enable debug messages and see more information after that.

Likely this is a problem with CUPS, not the driver for the printer.


Here's the most recent parts of the file:

```
W [17/Aug/2012:07:49:54 -0700] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/HP_LaserJet_Professional_P1102w_Gray__' has already been added
E [17/Aug/2012:14:34:00 -0700] Returning HTTP Forbidden for CUPS-Get-Devices (no URI) from localhost
I [17/Aug/2012:14:35:51 -0700] Listening to [v1.::1]:631 (IPv6)
I [17/Aug/2012:14:35:51 -0700] Listening to 127.0.0.1:631 (IPv4)
I [17/Aug/2012:14:35:51 -0700] Listening to /var/run/cups/cups.sock (Domain)
I [17/Aug/2012:14:35:51 -0700] Remote access is disabled.
D [17/Aug/2012:14:35:51 -0700] Added auto ServerAlias 5thAvenueBooks
I [17/Aug/2012:14:35:51 -0700] Loaded configuration file "/etc/cups/cupsd.conf"
I [17/Aug/2012:14:35:51 -0700] Using default TempDir of /var/spool/cups/tmp...
I [17/Aug/2012:14:35:51 -0700] Configured for up to 100 clients.
I [17/Aug/2012:14:35:51 -0700] Allowing up to 100 client connections per host.
I [17/Aug/2012:14:35:51 -0700] Using policy "default" as the default.
D [17/Aug/2012:14:35:51 -0700] load_ppd: Loading /var/cache/cups/HP-LaserJet-Professional-P1102w.data...
D [17/Aug/2012:14:35:51 -0700] Calling DeleteDevice(cups-HP-LaserJet-Professional-P1102w)
D [17/Aug/2012:14:35:51 -0700] failed to DeleteDevice: org.freedesktop.DBus.Error.InvalidArgs:Type of message, `(s)', does not match expected type `(o)'
D [17/Aug/2012:14:35:51 -0700] Using profile id of HP-LaserJet-Professional-P1102w-Gray..
D [17/Aug/2012:14:35:51 -0700] Calling CreateProfile(HP-LaserJet-Professional-P1102w-Gray..,temp)
D [17/Aug/2012:14:35:51 -0700] created profile /org/freedesktop/ColorManager/profiles/HP_LaserJet_Professional_P1102w_Gray__
I [17/Aug/2012:14:35:51 -0700] Registering ICC color profiles for "HP-LaserJet-Professional-P1102w"
D [17/Aug/2012:14:35:51 -0700] Calling CreateDevice(cups-HP-LaserJet-Professional-P1102w,temp)
D [17/Aug/2012:14:35:51 -0700] created device /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_Professional_P1102w
D [17/Aug/2012:14:35:51 -0700] Calling /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_Professional_P1102w:AddProfile(/org/freedesktop/ColorManager/profiles/HP_LaserJet_Professional_P1102w_Gray__) [soft]
W [17/Aug/2012:14:35:51 -0700] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/HP_LaserJet_Professional_P1102w_Gray__' has already been added
D [17/Aug/2012:14:35:51 -0700] cupsdRegisterPrinter(p=0x21db1308(HP-LaserJet-Professional-P1102w))
D [17/Aug/2012:14:35:51 -0700] cupsdMarkDirty(---p--)
D [17/Aug/2012:14:35:51 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Not busy"
I [17/Aug/2012:14:35:51 -0700] Partial reload complete.
I [17/Aug/2012:14:35:51 -0700] Listening to [v1.::1]:631 on fd 9...
I [17/Aug/2012:14:35:51 -0700] Listening to 127.0.0.1:631 on fd 10...
I [17/Aug/2012:14:35:51 -0700] Listening to /var/run/cups/cups.sock:631 on fd 11...
I [17/Aug/2012:14:35:51 -0700] Resuming new connection processing...
D [17/Aug/2012:14:35:51 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Aug/2012:14:35:51 -0700] Discarding unused server-restarted event...
D [17/Aug/2012:14:35:52 -0700] Report: clients=0
D [17/Aug/2012:14:35:52 -0700] Report: jobs=25
D [17/Aug/2012:14:35:52 -0700] Report: jobs-active=0
D [17/Aug/2012:14:35:52 -0700] Report: printers=1
D [17/Aug/2012:14:35:52 -0700] Report: printers-implicit=0
D [17/Aug/2012:14:35:52 -0700] Report: stringpool-string-count=18388
D [17/Aug/2012:14:35:52 -0700] Report: stringpool-alloc-bytes=9504
D [17/Aug/2012:14:35:52 -0700] Report: stringpool-total-bytes=326704
D [17/Aug/2012:14:35:56 -0700] cupsdAcceptClient: 15 from localhost:631 (IPv6)
D [17/Aug/2012:14:35:56 -0700] cupsdReadClient: 15 GET /admin/?OP=redirect&URL=/admin/?ADVANCEDSETTINGS=YES HTTP/1.1
D [17/Aug/2012:14:35:56 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Aug/2012:14:35:56 -0700] cupsdAuthorize: Authorized as elmarko using Basic
D [17/Aug/2012:14:35:56 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/admin.cgi"
D [17/Aug/2012:14:35:56 -0700] [CGI] argv[1] = "OP=redirect&URL=/admin/?ADVANCEDSETTINGS=YES"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@5thAvenueBooks"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.5.0"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[13] = "USER=root"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[14] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[15] = "CUPS_ENCRYPTION=IfRequested"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[16] = "IPP_PORT=631"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[17] = "AUTH_TYPE=Basic"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[18] = "LANG=en_US.UTF8"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[19] = "REDIRECT_STATUS=1"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[20] = "GATEWAY_INTERFACE=CGI/1.1"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[21] = "SERVER_NAME=localhost"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[22] = "SERVER_PORT=631"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[23] = "REMOTE_ADDR=[v1.::1]"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[24] = "REMOTE_HOST=localhost"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[25] = "SCRIPT_NAME=/admin/"
D [17/Aug/2012:14:35:56 -0700] [CGI] envp[26] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/admin/"
```

---

### Post by HumbleAmbition on 2012-08-24
Hi,

I have a very very similar problem. I installed the HP1102w printer with cups, no problems at first. I printed fine for two weeks and all of a sudden it stopped working last week. I've re-installed cups, fixed broken repositories, restarted the machine a hundred times. The trouble shooting logs is as follows:

D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:30 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:30 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:30 +0200] cupsdReadClient: 12 1.1 Get-Jobs 1
D [24/Aug/2012:15:55:30 +0200] Get-Jobs ipp://localhost/printers/
D [24/Aug/2012:15:55:30 +0200] [Job 166] Loading attributes...
D [24/Aug/2012:15:55:30 +0200] [Job 167] Loading attributes...
D [24/Aug/2012:15:55:30 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:30 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:30 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:30 +0200] cupsdReadClient: 12 1.1 Get-Jobs 1
D [24/Aug/2012:15:55:30 +0200] Get-Jobs ipp://localhost/printers/
D [24/Aug/2012:15:55:30 +0200] [Job 160] Loading attributes...
E [24/Aug/2012:15:55:30 +0200] [Job 160] Unable to queue job for destination "Hewlett-Packard-HP-LaserJet-Professional-P1102w"!
D [24/Aug/2012:15:55:30 +0200] [Job 161] Loading attributes...
E [24/Aug/2012:15:55:30 +0200] [Job 161] Unable to queue job for destination "Hewlett-Packard-HP-LaserJet-Professional-P1102w"!
D [24/Aug/2012:15:55:30 +0200] [Job 162] Loading attributes...
E [24/Aug/2012:15:55:30 +0200] [Job 162] Unable to queue job for destination "Hewlett-Packard-HP-LaserJet-Professional-P1102w"!
D [24/Aug/2012:15:55:30 +0200] [Job 163] Loading attributes...
D [24/Aug/2012:15:55:30 +0200] [Job 164] Loading attributes...
E [24/Aug/2012:15:55:30 +0200] [Job 164] Unable to queue job for destination "Hewlett-Packard-HP-LaserJet-Professional-P1102w"!
D [24/Aug/2012:15:55:30 +0200] [Job 165] Loading attributes...
E [24/Aug/2012:15:55:30 +0200] [Job 165] Unable to queue job for destination "Hewlett-Packard-HP-LaserJet-Professional-P1102w"!
D [24/Aug/2012:15:55:30 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:30 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:30 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:30 +0200] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [24/Aug/2012:15:55:30 +0200] Create-Printer-Subscription /
D [24/Aug/2012:15:55:30 +0200] cupsdCreateSubscription(con=0x21023148(12), uri="/")
D [24/Aug/2012:15:55:30 +0200] pullmethod="ippget"
D [24/Aug/2012:15:55:30 +0200] notify-lease-duration=86400
D [24/Aug/2012:15:55:30 +0200] notify-time-interval=0
D [24/Aug/2012:15:55:30 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [24/Aug/2012:15:55:30 +0200] Added subscription 81 for server
D [24/Aug/2012:15:55:30 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:30 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [24/Aug/2012:15:55:30 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:32 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:32 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:32 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:32 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:32 +0200] Get-Notifications /
D [24/Aug/2012:15:55:32 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:32 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:32 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:33 +0200] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2012:15:55:33 +0200] cupsdReadClient: 14 POST /printers/HP-LaserJet-Professional-P1102w HTTP/1.1
D [24/Aug/2012:15:55:33 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:33 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:33 +0200] cupsdReadClient: 14 1.1 Print-Job 1
D [24/Aug/2012:15:55:33 +0200] Print-Job ipp://localhost/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:33 +0200] [Job ???] Auto-typing file...
I [24/Aug/2012:15:55:33 +0200] [Job ???] Request file type is application/vnd.cups-banner.
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(----J-)
D [24/Aug/2012:15:55:33 +0200] add_job: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:33 +0200] Adding default job-sheets values "none,none"...
I [24/Aug/2012:15:55:33 +0200] [Job 168] Adding start banner page "none".
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(----J-)
I [24/Aug/2012:15:55:33 +0200] [Job 168] Adding end banner page "none".
I [24/Aug/2012:15:55:33 +0200] [Job 168] File of type application/vnd.cups-banner queued by "jennifer".
D [24/Aug/2012:15:55:33 +0200] [Job 168] hold_until=0
I [24/Aug/2012:15:55:33 +0200] [Job 168] Queued on "HP-LaserJet-Professional-P1102w" by "jennifer".
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(----J-)
D [24/Aug/2012:15:55:33 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:33 +0200] [Job 168] job-sheets=none,none
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[0]="HP-LaserJet-Professional-P1102w"
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[1]="168"
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[2]="jennifer"
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[3]="Test Page"
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[4]="1"
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[5]="job-uuid=urn:uuid:7541e883-e275-36e3-4ed4-ed0d265d2e94 nofitplot job-originating-host-name=localhost"
D [24/Aug/2012:15:55:33 +0200] [Job 168] argv[6]="/var/spool/cups/d00168-001"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[8]="HOME=/var/spool/cups/tmp"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[10]="SERVER_ADMIN=root@humbleambition"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[11]="SOFTWARE=CUPS/1.4.3"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[13]="TZ=Africa/Johannesburg"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[14]="USER=root"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[17]="IPP_PORT=631"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[18]="CHARSET=utf-8"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[19]="LANG=en_GB.UTF-8"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[20]="PPD=/etc/cups/ppd/HP-LaserJet-Professional-P1102w.ppd"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[21]="RIP_MAX_CACHE=765504k"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[23]="DEVICE_URI=usb://HP/LaserJet%20Professional%20P1102w"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[24]="PRINTER_INFO=Hewlett-Packard HP LaserJet Professional P1102w"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[25]="PRINTER_LOCATION=humbleambition"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[26]="PRINTER=HP-LaserJet-Professional-P1102w"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[27]="CUPS_FILETYPE=document"
D [24/Aug/2012:15:55:33 +0200] [Job 168] envp[28]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-Professional-P1102w"
I [24/Aug/2012:15:55:33 +0200] [Job 168] Started filter /usr/lib/cups/filter/bannertops (PID 31080)
I [24/Aug/2012:15:55:33 +0200] [Job 168] Started filter /usr/lib/cups/filter/pstopdf (PID 31081)
I [24/Aug/2012:15:55:33 +0200] [Job 168] Started filter /usr/lib/cups/filter/pdftopdf (PID 31082)
I [24/Aug/2012:15:55:33 +0200] [Job 168] Started filter /usr/lib/cups/filter/foomatic-rip (PID 31083)
I [24/Aug/2012:15:55:33 +0200] [Job 168] Started backend /usr/lib/cups/backend/usb (PID 31084)
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:33 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:33 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:33 +0200] [Job 168] load_banner(filename="/var/spool/cups/d00168-001")
D [24/Aug/2012:15:55:33 +0200] [Job 168] Getting input from file
D [24/Aug/2012:15:55:33 +0200] [Job 168] foomatic-rip version 4.0.4.217 running...
D [24/Aug/2012:15:55:33 +0200] [Job 168] Parsing PPD file ...
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option PageSize
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option Quality
D [24/Aug/2012:15:55:33 +0200] [Job 168] pstopdf 5 args: 168 jennifer Test Page 1 job-uuid=urn:uuid:7541e883-e275-36e3-4ed4-ed0d265d2e94 nofitplot job-originating-host-name=localhost
D [24/Aug/2012:15:55:33 +0200] [Job 168] PPD: /etc/cups/ppd/HP-LaserJet-Professional-P1102w.ppd
D [24/Aug/2012:15:55:33 +0200] [Job 168] STATE: +connecting-to-device
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option Resolution
D [24/Aug/2012:15:55:33 +0200] [Job 168] Page = 595x842; 11,11 to 584,831
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option ImageableArea
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option PaperDimension
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option InputSlot
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option MediaType
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option Density
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option Copies
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option halftone
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option NupOrient
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option NupPages
D [24/Aug/2012:15:55:33 +0200] [Job 168] Added option Font
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] Parameter Summary
D [24/Aug/2012:15:55:33 +0200] [Job 168] -----------------
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] Spooler: cups
D [24/Aug/2012:15:55:33 +0200] [Job 168] Printer: HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:33 +0200] [Job 168] Shell: /bin/bash
D [24/Aug/2012:15:55:33 +0200] [Job 168] PPD file: /etc/cups/ppd/HP-LaserJet-Professional-P1102w.ppd
D [24/Aug/2012:15:55:33 +0200] [Job 168] ATTR file:
D [24/Aug/2012:15:55:33 +0200] [Job 168] Printer model: HP LaserJet Pro P1102w Foomatic/foo2zjs-z2 (recommended)
D [24/Aug/2012:15:55:33 +0200] [Job 168] Job title: Test Page
D [24/Aug/2012:15:55:33 +0200] [Job 168] File(s) to be printed:
D [24/Aug/2012:15:55:33 +0200] [Job 168] <STDIN>
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [24/Aug/2012:15:55:33 +0200] [Job 168] Printing system options:
D [24/Aug/2012:15:55:33 +0200] [Job 168] Pondering option 'job-uuid=urn:uuid:7541e883-e275-36e3-4ed4-ed0d265d2e94'
D [24/Aug/2012:15:55:33 +0200] [Job 168] Unknown option job-uuid=urn:uuid:7541e883-e275-36e3-4ed4-ed0d265d2e94.
D [24/Aug/2012:15:55:33 +0200] [Job 168] Pondering option 'nofitplot'
D [24/Aug/2012:15:55:33 +0200] [Job 168] Unknown boolean option "nofitplot".
D [24/Aug/2012:15:55:33 +0200] [Job 168] Pondering option 'job-originating-host-name=localhost'
D [24/Aug/2012:15:55:33 +0200] [Job 168] Unknown option job-originating-host-name=localhost.
D [24/Aug/2012:15:55:33 +0200] [Job 168] Options from the PPD file:
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] ================================================
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] File: <STDIN>
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] ================================================
D [24/Aug/2012:15:55:33 +0200] [Job 168]
D [24/Aug/2012:15:55:33 +0200] [Job 168] Printer using device file "/dev/usblp0"...
D [24/Aug/2012:15:55:33 +0200] [Job 168] STATE: -connecting-to-device
D [24/Aug/2012:15:55:33 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:33 +0200] [Job 168] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0x610b40)
D [24/Aug/2012:15:55:33 +0200] [Job 168] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [24/Aug/2012:15:55:33 +0200] [Job 168] PNG image: 192x128x8, color_type=2 (RGB)
D [24/Aug/2012:15:55:33 +0200] PID 31080 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [24/Aug/2012:15:55:33 +0200] [Job 168] Resolution:
D [24/Aug/2012:15:55:33 +0200] [Job 168] Page size: A4
D [24/Aug/2012:15:55:33 +0200] [Job 168] Width: 595, height: 842, absolute margins: 11.34, 11.34, 583.66, 830.66
D [24/Aug/2012:15:55:33 +0200] [Job 168] Relative margins: 11.34, 11.34, 11.34, 11.34
D [24/Aug/2012:15:55:33 +0200] [Job 168] PPD options: -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [24/Aug/2012:15:55:33 +0200] [Job 168] PostScript to be injected:
D [24/Aug/2012:15:55:33 +0200] [Job 168] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sOutputFile=-  -c .setpdfwrite -f -
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 16 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:34 +0200] Get-Notifications /
D [24/Aug/2012:15:55:34 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Aug/2012:15:55:34 +0200] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 1.1 Get-Jobs 1
D [24/Aug/2012:15:55:34 +0200] Get-Jobs ipp://localhost/printers/
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [24/Aug/2012:15:55:34 +0200] cupsdCloseClient: 18
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:34 +0200] Get-Notifications /
D [24/Aug/2012:15:55:34 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [24/Aug/2012:15:55:34 +0200] Get-Job-Attributes ipp://localhost/jobs/168
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/168) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:34 +0200] Get-Notifications /
D [24/Aug/2012:15:55:34 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Aug/2012:15:55:34 +0200] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Aug/2012:15:55:34 +0200] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 16 WAITING Closing on EOF
D [24/Aug/2012:15:55:34 +0200] cupsdCloseClient: 16
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Printers
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Classes
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Default
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Printers
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Classes
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Default
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Printers
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Classes
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Default
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [24/Aug/2012:15:55:34 +0200] cupsdCloseClient: 18
D [24/Aug/2012:15:55:34 +0200] PID 31081 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [24/Aug/2012:15:55:34 +0200] [Job 168] Filetype: PDF
D [24/Aug/2012:15:55:34 +0200] [Job 168] Driver does not understand PDF input, converting to PostScript
D [24/Aug/2012:15:55:34 +0200] [Job 168] Storing temporary files in /var/spool/cups/tmp
D [24/Aug/2012:15:55:34 +0200] PID 31082 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "pdf-to-ps" (generation 1)
D [24/Aug/2012:15:55:34 +0200] [Job 168] Filetype: PostScript
D [24/Aug/2012:15:55:34 +0200] [Job 168] Reading PostScript input ...
D [24/Aug/2012:15:55:34 +0200] [Job 168] --> This document is DSC-conforming!
D [24/Aug/2012:15:55:34 +0200] [Job 168] Job claims to be DSC-conforming, but "%%BeginProlog" was missing before first line with another"%%BeginProlog" comment (is this a TeX/LaTeX/dvips-generated PostScript file?). Assuming start of "Prolog" here.
D [24/Aug/2012:15:55:34 +0200] [Job 168] Inserting option code into "Prolog" section.
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] -----------
D [24/Aug/2012:15:55:34 +0200] [Job 168] Found: %%BeginProlog
D [24/Aug/2012:15:55:34 +0200] [Job 168] Found: %%EndProlog
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] -----------
D [24/Aug/2012:15:55:34 +0200] [Job 168] Found: %%BeginSetup
D [24/Aug/2012:15:55:34 +0200] [Job 168] Found: %%EndSetup
D [24/Aug/2012:15:55:34 +0200] [Job 168] Inserting PostScript code for CUPS' page accounting
D [24/Aug/2012:15:55:34 +0200] [Job 168] Inserting option code into "Setup" section.
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] -----------
D [24/Aug/2012:15:55:34 +0200] [Job 168] New page: %%Page: 1 1
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] Found: %%BeginPageSetup
D [24/Aug/2012:15:55:34 +0200] [Job 168] Inserting option code into "PageSetup" section.
D [24/Aug/2012:15:55:34 +0200] [Job 168] Flushing FIFO.
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting renderer with command: "foo2zjs-wrapper -z2 -P -L0     -r1200x600 -p9 -T2 -m1 -s7   -n1 "
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "kid3" (generation 1)
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] Closing renderer
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "kid4" (generation 2)
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "renderer" (generation 2)
D [24/Aug/2012:15:55:34 +0200] [Job 168] JCL: %-12345X@PJL
D [24/Aug/2012:15:55:34 +0200] [Job 168] <job data>
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] Illegal option -T
D [24/Aug/2012:15:55:34 +0200] [Job 168] renderer exited with status 1
D [24/Aug/2012:15:55:34 +0200] [Job 168] Possible error on renderer command line or PostScript error. Check options.kid3 exited with status 3
D [24/Aug/2012:15:55:34 +0200] [Job 168] Process is dying with "Error closing renderer
D [24/Aug/2012:15:55:34 +0200] [Job 168] ", exit stat 3
D [24/Aug/2012:15:55:34 +0200] [Job 168] Cleaning up...
D [24/Aug/2012:15:55:34 +0200] [Job 168] Killing pdf-to-ps
D [24/Aug/2012:15:55:34 +0200] [Job 168] Read 2975 bytes of print data...
D [24/Aug/2012:15:55:34 +0200] [Job 168] STATE: -media-empty-warning
D [24/Aug/2012:15:55:34 +0200] [Job 168] STATE: -offline-report
I [24/Aug/2012:15:55:34 +0200] [Job 168] Printer is now online.
D [24/Aug/2012:15:55:34 +0200] [Job 168] Wrote 2975 bytes of print data...
D [24/Aug/2012:15:55:34 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:34 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 16 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:34 +0200] Get-Notifications /
D [24/Aug/2012:15:55:34 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 1.1 Get-Jobs 1
D [24/Aug/2012:15:55:34 +0200] Get-Jobs ipp://localhost/printers/
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [24/Aug/2012:15:55:34 +0200] cupsdCloseClient: 18
D [24/Aug/2012:15:55:34 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:34 +0200] Get-Notifications /
D [24/Aug/2012:15:55:34 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Aug/2012:15:55:34 +0200] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:34 +0200] Get-Notifications /
D [24/Aug/2012:15:55:34 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 16 WAITING Closing on EOF
D [24/Aug/2012:15:55:34 +0200] cupsdCloseClient: 16
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Printers
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Classes
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [24/Aug/2012:15:55:34 +0200] CUPS-Get-Default
D [24/Aug/2012:15:55:34 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Aug/2012:15:55:34 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [24/Aug/2012:15:55:34 +0200] cupsdReadClient: 18 WAITING Closing on EOF
D [24/Aug/2012:15:55:34 +0200] cupsdCloseClient: 18
D [24/Aug/2012:15:55:42 +0200] PID 31083 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
D [24/Aug/2012:15:55:42 +0200] PID 31084 (/usr/lib/cups/backend/usb) exited with no errors.
D [24/Aug/2012:15:55:42 +0200] cupsdMarkDirty(-----S)
E [24/Aug/2012:15:55:42 +0200] [Job 168] Job stopped due to filter errors; please consult the error_log file for details.
D [24/Aug/2012:15:55:42 +0200] cupsdMarkDirty(----J-)
D [24/Aug/2012:15:55:42 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:42 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 15 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 15 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:42 +0200] Get-Notifications /
D [24/Aug/2012:15:55:42 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Aug/2012:15:55:42 +0200] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 16 1.1 Get-Jobs 1
D [24/Aug/2012:15:55:42 +0200] Get-Jobs ipp://localhost/printers/
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 16 WAITING Closing on EOF
D [24/Aug/2012:15:55:42 +0200] cupsdCloseClient: 16
D [24/Aug/2012:15:55:42 +0200] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 16 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:42 +0200] Get-Notifications /
D [24/Aug/2012:15:55:42 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [24/Aug/2012:15:55:42 +0200] Get-Printer-Attributes ipp://humbleambition:0/printers/HP-LaserJet-Professional-P1102w
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://humbleambition:0/printers/HP-LaserJet-Professional-P1102w) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [24/Aug/2012:15:55:42 +0200] Get-Job-Attributes ipp://localhost/jobs/168
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/168) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 15 WAITING Closing on EOF
D [24/Aug/2012:15:55:42 +0200] cupsdCloseClient: 15
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [24/Aug/2012:15:55:42 +0200] CUPS-Get-Printers
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [24/Aug/2012:15:55:42 +0200] CUPS-Get-Classes
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [24/Aug/2012:15:55:42 +0200] CUPS-Get-Default
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1
D [24/Aug/2012:15:55:42 +0200] Get-Notifications /
D [24/Aug/2012:15:55:42 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:42 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Aug/2012:15:55:42 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:42 +0200] cupsdReadClient: 16 WAITING Closing on EOF
D [24/Aug/2012:15:55:42 +0200] cupsdCloseClient: 16
D [24/Aug/2012:15:55:43 +0200] [Job 168] Unloading...
D [24/Aug/2012:15:55:47 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:47 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:47 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:47 +0200] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [24/Aug/2012:15:55:47 +0200] Get-Job-Attributes ipp://localhost/jobs/168
D [24/Aug/2012:15:55:47 +0200] [Job 168] Loading attributes...
D [24/Aug/2012:15:55:47 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/168) from localhost
D [24/Aug/2012:15:55:47 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:47 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Aug/2012:15:55:47 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:47 +0200] cupsdAuthorize: No authentication data provided.
D [24/Aug/2012:15:55:47 +0200] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [24/Aug/2012:15:55:47 +0200] Cancel-Subscription /
D [24/Aug/2012:15:55:47 +0200] cupsdIsAuthorized: requesting-user-name="jennifer"
D [24/Aug/2012:15:55:47 +0200] cupsdMarkDirty(-----S)
D [24/Aug/2012:15:55:47 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [24/Aug/2012:15:55:47 +0200] cupsdSetBusyState: Dirty files
D [24/Aug/2012:15:55:47 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [24/Aug/2012:15:55:47 +0200] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [24/Aug/2012:15:55:47 +0200] cupsdSetBusyState: Active clients and dirty files
D [24/Aug/2012:15:55:47 +0200] cupsdAuthorize: No authentication data provided.




Any help would be greatly appreciated!

---

### Post by aikishugyo on 2012-08-25
Clearly the pdftops filter is not working:

> D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting renderer with command: "foo2zjs-wrapper -z2 -P -L0 -r1200x600 -p9 -T2 -m1 -s7 -n1 "
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "kid3" (generation 1)
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] Closing renderer
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "kid4" (generation 2)
D [24/Aug/2012:15:55:34 +0200] [Job 168] Starting process "renderer" (generation 2)
D [24/Aug/2012:15:55:34 +0200] [Job 168] JCL: %-12345X@PJL
D [24/Aug/2012:15:55:34 +0200] [Job 168] <job data>
D [24/Aug/2012:15:55:34 +0200] [Job 168]
D [24/Aug/2012:15:55:34 +0200] [Job 168] Illegal option -T
D [24/Aug/2012:15:55:34 +0200] [Job 168] renderer exited with status 1
D [24/Aug/2012:15:55:34 +0200] [Job 168] Possible error on renderer command line or PostScript error. Check options.kid3 exited with status 3
D [24/Aug/2012:15:55:34 +0200] [Job 168] Process is dying with "Error closing renderer
D [24/Aug/2012:15:55:34 +0200] [Job 168] ", exit stat 3
D [24/Aug/2012:15:55:34 +0200] [Job 168] Cleaning up...
D [24/Aug/2012:15:55:34 +0200] [Job 168] Killing pdf-to-ps

So probably you need to check the the cups mailing list archives to see what has been said recently about pdftops conversions. This is handled by openprinting I believe.

---


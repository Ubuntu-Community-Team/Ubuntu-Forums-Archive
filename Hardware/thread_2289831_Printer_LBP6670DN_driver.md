---
title: "Printer LBP6670DN driver"
date: 2015-08-07
forum: Hardware
---

### Post by alain.roger on 2015-08-07
Hi,

At home, i have a Canon printer LBP 6670dn as network printer using it's own IP address.
I'm using Kubuntu 15.04 and i'm trying to make it work under Kubuntu 15.04 (x64) but without success.

I downloaded drivers from [http://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp6670dn.aspx?type=drivers&language=EN&os=Linux%20(64-bit)](http://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp6670dn.aspx?type=drivers&language=EN&os=Linux%20(64-bit)) and printer is correctly installed.
[ATTACH=CONFIG]263708[/ATTACH]

However, when i try to print a test page, the queue shows a failure status. Why ?
[ATTACH=CONFIG]263707[/ATTACH]
thx.

---

### Post by howefield on 2015-08-07
Have a look in /var/log/cups for clues to the problem.

Or try creating another printer with a different name and see if it works. If it does then delete the old one.

---

### Post by alain.roger on 2015-08-08
So firstly, i check if i can find the network printer with a ping.

result:
package are correctly sent to 192.168.1.200 (network printer)

Next i did: /usr/lib/cups/backend/snmp

result:         [FONT=monospace][COLOR=#000000]network socket://192.168.1.200 "Canon LBP6670 UFR II" "Canon LBP6670" "MFG:Canon;MDL:LBP6670 UFR II;CLS:PRINTER;DES:Canon LBP6670;CID:;CMD:LIPSLX,PCL,CPCA;" ""[/COLOR]
[/FONT]
   
next i did: sudo /usr/lib/cups/backend/dnssd

result:
       [FONT=monospace][COLOR=#000000]DEBUG: sent=0, count=0 [/COLOR]
DEBUG: sent=0, count=0 
DEBUG: sent=0, count=0

[/FONT]
   next i did: lpinfo -v

result:
...
 [FONT=monospace][COLOR=#000000]network socket://192.168.1.200[/COLOR]

[/FONT]
Next i did:
avahi-browse -a -v -t -r
and
avahi-browse -a -v -c -r

Result:
nothing relative to printer, but only to my PC


Here is the error.log file content once i did:  [FONT=monospace][COLOR=#000000]cupsctl LogLevel=debug[/COLOR]



> I [08/Aug/2015:14:29:51 +0200] Listening to [v1.::1]:631 (IPv6)
I [08/Aug/2015:14:29:51 +0200] Listening to 127.0.0.1:631 (IPv4)
I [08/Aug/2015:14:29:51 +0200] Remote access is disabled.
D [08/Aug/2015:14:29:51 +0200] Added auto ServerAlias pc0001
I [08/Aug/2015:14:29:51 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
D [08/Aug/2015:14:29:51 +0200] Using keychain "/etc/cups/ssl" for server name "pc0001".
I [08/Aug/2015:14:29:51 +0200] Configured for up to 100 clients.
I [08/Aug/2015:14:29:51 +0200] Allowing up to 100 client connections per host.
I [08/Aug/2015:14:29:51 +0200] Using policy "default" as the default.
D [08/Aug/2015:14:29:51 +0200] load_ppd: Loading /var/cache/cups/CanonLBP6670dn.data...
D [08/Aug/2015:14:29:51 +0200] cupsdRegisterPrinter(p=0x7f5ec0a3f6d0(CanonLBP6670dn))
D [08/Aug/2015:14:29:52 +0200] load_ppd: Loading /var/cache/cups/MP610-series.data...
D [08/Aug/2015:14:29:52 +0200] cupsdRegisterPrinter(p=0x7f5ec0a55dc0(MP610-series))
D [08/Aug/2015:14:29:52 +0200] cupsdMarkDirty(--p--)
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Not busy"
I [08/Aug/2015:14:29:52 +0200] Partial reload complete.
D [08/Aug/2015:14:29:52 +0200] Calling FindDeviceById(cups-CanonLBP6670dn)
D [08/Aug/2015:14:29:52 +0200] Calling DeleteDevice(/org/freedesktop/ColorManager/devices/cups_CanonLBP6670dn)
D [08/Aug/2015:14:29:52 +0200] Using profile ID "CanonLBP6670dn-Gray..".
D [08/Aug/2015:14:29:52 +0200] Calling CreateProfile(CanonLBP6670dn-Gray..,temp)
W [08/Aug/2015:14:29:52 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:razz:rofile id 'CanonLBP6670dn-Gray..' already exists
I [08/Aug/2015:14:29:52 +0200] Registering ICC color profiles for "CanonLBP6670dn".
D [08/Aug/2015:14:29:52 +0200] Calling CreateDevice(cups-CanonLBP6670dn,temp)
D [08/Aug/2015:14:29:52 +0200] Created device "/org/freedesktop/ColorManager/devices/cups_CanonLBP6670dn".
D [08/Aug/2015:14:29:52 +0200] Calling FindDeviceById(cups-MP610-series)
D [08/Aug/2015:14:29:52 +0200] Calling DeleteDevice(/org/freedesktop/ColorManager/devices/cups_MP610_series)
D [08/Aug/2015:14:29:52 +0200] Using profile ID "MP610-series-Gray..".
D [08/Aug/2015:14:29:52 +0200] Calling CreateProfile(MP610-series-Gray..,temp)
W [08/Aug/2015:14:29:52 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:razz:rofile id 'MP610-series-Gray..' already exists
D [08/Aug/2015:14:29:52 +0200] Using profile ID "MP610-series-RGB..".
D [08/Aug/2015:14:29:52 +0200] Calling CreateProfile(MP610-series-RGB..,temp)
W [08/Aug/2015:14:29:52 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:razz:rofile id 'MP610-series-RGB..' already exists
I [08/Aug/2015:14:29:52 +0200] Registering ICC color profiles for "MP610-series".
D [08/Aug/2015:14:29:52 +0200] Calling CreateDevice(cups-MP610-series,temp)
D [08/Aug/2015:14:29:52 +0200] Created device "/org/freedesktop/ColorManager/devices/cups_MP610_series".
I [08/Aug/2015:14:29:52 +0200] Listening to /var/run/cups/cups.sock on fd 3...
I [08/Aug/2015:14:29:52 +0200] Listening to [v1.::1]:631 on fd 10...
I [08/Aug/2015:14:29:52 +0200] Listening to 127.0.0.1:631 on fd 11...
I [08/Aug/2015:14:29:52 +0200] Resuming new connection processing...
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [08/Aug/2015:14:29:52 +0200] Notifier dbus started - PID = 22559
D [08/Aug/2015:14:29:52 +0200] Notifier dbus started - PID = 22560
D [08/Aug/2015:14:29:52 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [08/Aug/2015:14:29:52 +0200] [Notifier] state=3
D [08/Aug/2015:14:29:52 +0200] Report: clients=0
D [08/Aug/2015:14:29:52 +0200] Report: jobs=9
D [08/Aug/2015:14:29:52 +0200] Report: jobs-active=1
D [08/Aug/2015:14:29:52 +0200] Report: printers=2
D [08/Aug/2015:14:29:52 +0200] Report: stringpool-string-count=92730
D [08/Aug/2015:14:29:52 +0200] Report: stringpool-alloc-bytes=14280
D [08/Aug/2015:14:29:52 +0200] Report: stringpool-total-bytes=1731360
D [08/Aug/2015:14:29:52 +0200] PID 7270 (/usr/lib/cups/notifier/dbus) exited with no errors.
D [08/Aug/2015:14:29:52 +0200] PID 7271 (/usr/lib/cups/notifier/dbus) was terminated normally with signal 15.
D [08/Aug/2015:14:29:52 +0200] [Notifier] state=3
D [08/Aug/2015:14:29:52 +0200] [Notifier] Connected to D-BUS
D [08/Aug/2015:14:29:52 +0200] [Notifier] ServerRestarted
D [08/Aug/2015:14:29:52 +0200] [Notifier] Connected to D-BUS
D [08/Aug/2015:14:29:52 +0200] [Client 38] Accepted from localhost:44108 (IPv6)
D [08/Aug/2015:14:29:52 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:29:52 +0200] cupsdAddCert: Adding certificate for PID 0
D [08/Aug/2015:14:29:52 +0200] [Client 39] Accepted from localhost:44109 (IPv6)
D [08/Aug/2015:14:29:52 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:29:52 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:29:52 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:29:52 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:29:52 +0200] [Client 38] 2.0 Get-Jobs 17
D [08/Aug/2015:14:29:52 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:29:52 +0200] [Job 9] Loading attributes...
D [08/Aug/2015:14:29:52 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:29:52 +0200] [Client 38] Content-Length: 487
D [08/Aug/2015:14:29:52 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:29:52 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:29:52 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=487, response=0x7f5ec0a88370(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:29:52 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:29:52 +0200] [Client 38] bytes=0, http_state=0, data_remaining=487
D [08/Aug/2015:14:29:52 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:29:52 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:29:52 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:29:52 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:29:52 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:29:52 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:29:52 +0200] [Client 39] 2.0 Get-Jobs 18
D [08/Aug/2015:14:29:52 +0200] Get-Jobs ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:29:52 +0200] [Client 39] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/CanonLBP6670dn) from  localhost
D [08/Aug/2015:14:29:52 +0200] [Client 39] Content-Length: 487
D [08/Aug/2015:14:29:52 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:29:52 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:29:52 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:29:52 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:29:52 +0200] [Client 38] 2.0 Get-Jobs 18
D [08/Aug/2015:14:29:52 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:29:52 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:29:52 +0200] [Client 38] Content-Length: 487
D [08/Aug/2015:14:29:52 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:29:52 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:29:52 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=487, response=0x7f5ec0a88cc0(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:29:52 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:29:52 +0200] [Client 39] bytes=0, http_state=0, data_remaining=487
D [08/Aug/2015:14:29:52 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:29:52 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:29:52 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:29:52 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:29:52 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=487, response=0x7f5ec10d8400(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:29:52 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:29:52 +0200] [Client 38] bytes=0, http_state=0, data_remaining=487
D [08/Aug/2015:14:29:52 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:29:52 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:29:52 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:29:52 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 40] Accepted from localhost:44114 (IPv6)
D [08/Aug/2015:14:30:08 +0200] [Client 40] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] [Client 40] POST / HTTP/1.1
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 40] Read: status=200
D [08/Aug/2015:14:30:08 +0200] [Client 40] No authentication data provided.
D [08/Aug/2015:14:30:08 +0200] [Client 40] 2.0 CUPS-Get-Printers 1
D [08/Aug/2015:14:30:08 +0200] CUPS-Get-Printers
D [08/Aug/2015:14:30:08 +0200] [Client 40] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [08/Aug/2015:14:30:08 +0200] [Client 40] Content-Length: 892
D [08/Aug/2015:14:30:08 +0200] [Client 40] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:08 +0200] [Client 40] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:08 +0200] [Client 40] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=892, response=0x7f5ec0a88300(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:08 +0200] [Client 40] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:08 +0200] [Client 40] bytes=0, http_state=0, data_remaining=892
D [08/Aug/2015:14:30:08 +0200] [Client 40] Flushing write buffer.
D [08/Aug/2015:14:30:08 +0200] [Client 40] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:08 +0200] [Client 40] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 40] POST / HTTP/1.1
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 40] Read: status=200
D [08/Aug/2015:14:30:08 +0200] [Client 40] No authentication data provided.
D [08/Aug/2015:14:30:08 +0200] [Client 40] 2.0 CUPS-Get-Printers 2
D [08/Aug/2015:14:30:08 +0200] CUPS-Get-Printers
D [08/Aug/2015:14:30:08 +0200] [Client 40] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [08/Aug/2015:14:30:08 +0200] [Client 40] Content-Length: 892
D [08/Aug/2015:14:30:08 +0200] [Client 40] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:08 +0200] [Client 40] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:08 +0200] [Client 40] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=892, response=0x7f5ec0f30cc0(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:08 +0200] [Client 40] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:08 +0200] [Client 40] bytes=0, http_state=0, data_remaining=892
D [08/Aug/2015:14:30:08 +0200] [Client 40] Flushing write buffer.
D [08/Aug/2015:14:30:08 +0200] [Client 40] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:08 +0200] [Client 40] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 40] GET /admin/conf/cupsd.conf HTTP/1.1
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 40] Read: status=200
D [08/Aug/2015:14:30:08 +0200] [Client 40] No authentication data provided.
D [08/Aug/2015:14:30:08 +0200] cupsdIsAuthorized: username=""
D [08/Aug/2015:14:30:08 +0200] [Client 40] cupsdSendHeader: code=401, type="text/html", auth_type=0
D [08/Aug/2015:14:30:08 +0200] [Client 40] WWW-Authenticate: Basic realm="CUPS", trc="y"
D [08/Aug/2015:14:30:08 +0200] [Client 40] Closing connection.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 41] Accepted from localhost:44115 (IPv6)
D [08/Aug/2015:14:30:08 +0200] [Client 41] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] [Client 42] Accepted from localhost:44116 (IPv6)
D [08/Aug/2015:14:30:08 +0200] [Client 42] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] [Client 41] HTTP_STATE_WAITING Closing for error 32 (Broken pipe)
D [08/Aug/2015:14:30:08 +0200] [Client 41] Closing connection.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 43] Accepted from localhost:44117 (IPv6)
D [08/Aug/2015:14:30:08 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] [Client 42] HTTP_STATE_WAITING Closing for error 32 (Broken pipe)
D [08/Aug/2015:14:30:08 +0200] [Client 42] Closing connection.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 43] GET /admin/conf/cupsd.conf HTTP/1.1
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 43] Read: status=200
D [08/Aug/2015:14:30:08 +0200] [Client 43] Authorized as root using Local
D [08/Aug/2015:14:30:08 +0200] cupsdIsAuthorized: username="root"
D [08/Aug/2015:14:30:08 +0200] [Client 43] Processing GET /admin/conf/cupsd.conf
D [08/Aug/2015:14:30:08 +0200] [Client 43] filename="/etc/cups/cupsd.conf", type=text/plain
D [08/Aug/2015:14:30:08 +0200] [Client 43] cupsdSendHeader: code=200, type="text/plain", auth_type=0
D [08/Aug/2015:14:30:08 +0200] [Client 43] Sending file.
D [08/Aug/2015:14:30:08 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:08 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=3090, response=(nil)(), pipe_pid=0, file=21
D [08/Aug/2015:14:30:08 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:08 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=3090, response=(nil)(), pipe_pid=0, file=21
D [08/Aug/2015:14:30:08 +0200] [Client 43] Flushing write buffer.
D [08/Aug/2015:14:30:08 +0200] [Client 43] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:08 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 43] POST / HTTP/1.1
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 43] Read: status=200
D [08/Aug/2015:14:30:08 +0200] [Client 43] No authentication data provided.
D [08/Aug/2015:14:30:08 +0200] [Client 43] 2.0 Create-Printer-Subscriptions 3
D [08/Aug/2015:14:30:08 +0200] Create-Printer-Subscriptions /
D [08/Aug/2015:14:30:08 +0200] create_subscriptions(con=0x7f5ec10d7f50(43), uri="/")
D [08/Aug/2015:14:30:08 +0200] recipient="dbus://"
D [08/Aug/2015:14:30:08 +0200] pullmethod="ippget"
D [08/Aug/2015:14:30:08 +0200] notify-lease-duration=3600
D [08/Aug/2015:14:30:08 +0200] notify-time-interval=0
D [08/Aug/2015:14:30:08 +0200] cupsdAddSubscription(mask=1e038f, dest=(nil)(), job=(nil)(0), uri="dbus://")
D [08/Aug/2015:14:30:08 +0200] Added subscription #61 for server.
D [08/Aug/2015:14:30:08 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:08 +0200] [Client 43] Returning IPP successful-ok for Create-Printer-Subscriptions (/) from localhost
D [08/Aug/2015:14:30:08 +0200] [Client 43] Content-Length: 107
D [08/Aug/2015:14:30:08 +0200] [Client 43] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:08 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:08 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=107, response=0x7f5ec0a883c0(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:08 +0200] [Client 43] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:08 +0200] [Client 43] bytes=0, http_state=0, data_remaining=107
D [08/Aug/2015:14:30:08 +0200] [Client 43] Flushing write buffer.
D [08/Aug/2015:14:30:08 +0200] [Client 43] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:08 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:08 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 43] POST /printers/CanonLBP6670dn HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 43] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 43] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 43] 2.0 Print-Job 4
D [08/Aug/2015:14:30:12 +0200] Print-Job ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Job ???] Auto-typing file...
I [08/Aug/2015:14:30:12 +0200] [Job ???] Request file type is application/vnd.cups-pdf-banner.
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(---J-)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] add_job: requesting-user-name="alain"
D [08/Aug/2015:14:30:12 +0200] Adding default job-sheets values "none,none"...
I [08/Aug/2015:14:30:12 +0200] [Job 10] Adding start banner page "none".
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(---J-)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
I [08/Aug/2015:14:30:12 +0200] [Job 10] Adding end banner page "none".
I [08/Aug/2015:14:30:12 +0200] [Job 10] File of type application/vnd.cups-pdf-banner queued by "alain".
D [08/Aug/2015:14:30:12 +0200] [Job 10] hold_until=0
I [08/Aug/2015:14:30:12 +0200] [Job 10] Queued on "CanonLBP6670dn" by "alain".
D [08/Aug/2015:14:30:12 +0200] [Job 10] time-at-processing=1439037012
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(---J-)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] Notifier dbus started - PID = 22566
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Job 10] 3 filters for job:
D [08/Aug/2015:14:30:12 +0200] [Job 10] bannertopdf (application/vnd.cups-pdf-banner to application/pdf, cost 32)
D [08/Aug/2015:14:30:12 +0200] [Job 10] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [08/Aug/2015:14:30:12 +0200] [Job 10] foomatic-rip (application/vnd.cups-pdf to printer/CanonLBP6670dn, cost 0)
D [08/Aug/2015:14:30:12 +0200] [Job 10] job-sheets=none,none
D [08/Aug/2015:14:30:12 +0200] [Job 10] argv[0]="CanonLBP6670dn"
D [08/Aug/2015:14:30:12 +0200] [Job 10] argv[1]="10"
D [08/Aug/2015:14:30:12 +0200] [Job 10] argv[2]="alain"
D [08/Aug/2015:14:30:12 +0200] [Job 10] argv[3]="Test Page"
D [08/Aug/2015:14:30:12 +0200] [Job 10] argv[4]="1"
D [08/Aug/2015:14:30:12 +0200] [Job 10]  argv[5]="job-uuid=urn:uuid:9b7bb467-53ee-3a81-430a-c4c85c7df805  job-originating-host-name=localhost time-at-creation=1439037012  time-at-processing=1439037012"
D [08/Aug/2015:14:30:12 +0200] [Job 10] argv[6]="/var/spool/cups/d00010-001"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[8]="HOME=/var/spool/cups/tmp"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[10]="SERVER_ADMIN=root@pc0001"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[11]="SOFTWARE=CUPS/2.0.2"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[13]="USER=root"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[14]="CUPS_MAX_MESSAGE=2047"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[17]="IPP_PORT=631"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[18]="CHARSET=utf-8"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[19]="LANG=en_US.UTF-8"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[20]="PPD=/etc/cups/ppd/CanonLBP6670dn.ppd"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[21]="RIP_MAX_CACHE=128m"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[23]="DEVICE_URI=http://192.168.1.200"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[24]="PRINTER_INFO=Network Laser Printer HOME"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[25]="PRINTER_LOCATION="
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[26]="PRINTER=CanonLBP6670dn"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[27]="PRINTER_STATE_REASONS=none"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[28]="CUPS_FILETYPE=document"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
D [08/Aug/2015:14:30:12 +0200] [Job 10] envp[30]="AUTH_I****"
I [08/Aug/2015:14:30:12 +0200] [Job 10] Started filter /usr/lib/cups/filter/bannertopdf (PID 22567)
I [08/Aug/2015:14:30:12 +0200] [Job 10] Started filter /usr/lib/cups/filter/pdftopdf (PID 22568)
I [08/Aug/2015:14:30:12 +0200] [Job 10] Started filter /usr/lib/cups/filter/foomatic-rip (PID 22569)
I [08/Aug/2015:14:30:12 +0200] [Job 10] Started backend /usr/lib/cups/backend/http (PID 22570)
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients and dirty  files"
D [08/Aug/2015:14:30:12 +0200] [Client 43] Returning IPP successful-ok  for Print-Job (ipp://alain@localhost:631/printers/CanonLBP6670dn) from  localhost
D [08/Aug/2015:14:30:12 +0200] [Client 43] Content-Length: 174
D [08/Aug/2015:14:30:12 +0200] [Client 43] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:12 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=174, response=0x7f5ec0f30cc0(IPP_STATE_IDLE), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 43] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 43] bytes=0, http_state=0, data_remaining=174
D [08/Aug/2015:14:30:12 +0200] [Client 43] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 43] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Printing jobs  and dirty files", busy="Active clients, printing jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Notifier] JobCreated
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Notifier] JobState
D [08/Aug/2015:14:30:12 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Printing jobs and dirty  files"
D [08/Aug/2015:14:30:12 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 39] 2.0 Get-Jobs 19
D [08/Aug/2015:14:30:12 +0200] Get-Jobs ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Client 39] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/CanonLBP6670dn) from  localhost
D [08/Aug/2015:14:30:12 +0200] [Client 39] Content-Length: 837
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients, printing  jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 38] 2.0 Get-Jobs 19
D [08/Aug/2015:14:30:12 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:30:12 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 38] Content-Length: 837
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 43] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients, printing  jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 43] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 43] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 43] 2.0 Get-Printer-Attributes 5
D [08/Aug/2015:14:30:12 +0200] Get-Printer-Attributes ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Client 43] Returning IPP successful-ok  for Get-Printer-Attributes  (ipp://alain@localhost:631/printers/CanonLBP6670dn) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 43] Content-Length: 541
D [08/Aug/2015:14:30:12 +0200] [Client 43] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=837, response=0x7f5ec0d63910(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] bytes=0, http_state=0, data_remaining=837
D [08/Aug/2015:14:30:12 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients, printing  jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=837, response=0x7f5ec0a39180(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] bytes=0, http_state=0, data_remaining=837
D [08/Aug/2015:14:30:12 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients, printing  jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:12 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=541, response=0x7f5ec0a39bf0(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 43] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 43] bytes=0, http_state=0, data_remaining=541
D [08/Aug/2015:14:30:12 +0200] [Client 43] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 43] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Printing jobs  and dirty files", busy="Active clients, printing jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Printing jobs and dirty  files"
D [08/Aug/2015:14:30:12 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 39] 2.0 Get-Printer-Attributes 20
D [08/Aug/2015:14:30:12 +0200] Get-Printer-Attributes ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Client 39] Returning IPP successful-ok  for Get-Printer-Attributes  (ipp://alain@localhost:631/printers/CanonLBP6670dn) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 39] Content-Length: 188
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients, printing  jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 38] 2.0 Get-Jobs 20
D [08/Aug/2015:14:30:12 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:30:12 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 38] Content-Length: 837
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=188, response=0x7f5ec0a39250(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] bytes=0, http_state=0, data_remaining=188
D [08/Aug/2015:14:30:12 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Active clients, printing  jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=837, response=0x7f5ec0a38720(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] bytes=0, http_state=0, data_remaining=837
D [08/Aug/2015:14:30:12 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Printing jobs  and dirty files", busy="Active clients, printing jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active  clients, printing jobs, and dirty files", busy="Printing jobs and dirty  files"
D [08/Aug/2015:14:30:12 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 39] 2.0 Get-Jobs 21
D [08/Aug/2015:14:30:12 +0200] Get-Jobs ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Client 39] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/CanonLBP6670dn) from  localhost
D [08/Aug/2015:14:30:12 +0200] [Client 39] Content-Length: 837
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=837, response=0x7f5ec0a39180(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] bytes=0, http_state=0, data_remaining=837
D [08/Aug/2015:14:30:12 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Printing jobs  and dirty files", busy="Active clients, printing jobs, and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Job 10] Sending stdin for job...
D [08/Aug/2015:14:30:12 +0200] [Job 10] update_reasons(attr=0(), s="+connecting-to-device")
D [08/Aug/2015:14:30:12 +0200] [Job 10] STATE: +connecting-to-device
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(---J-)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Job 10] Looking up "192.168.1.200"...
D [08/Aug/2015:14:30:12 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:12 +0200] [Notifier] Connected to D-BUS
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:12 +0200] [Client 43] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 43] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 43] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 43] 2.0 Get-Printer-Attributes 6
D [08/Aug/2015:14:30:12 +0200] Get-Printer-Attributes ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Client 43] Returning IPP successful-ok  for Get-Printer-Attributes  (ipp://alain@localhost:631/printers/CanonLBP6670dn) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 43] Content-Length: 541
D [08/Aug/2015:14:30:12 +0200] [Client 43] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:12 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=541, response=0x7f5ec0f30cc0(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 43] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 43] bytes=0, http_state=0, data_remaining=541
D [08/Aug/2015:14:30:12 +0200] [Client 43] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 43] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Job 10] Calling FindDeviceById(cups-CanonLBP6670dn)
D [08/Aug/2015:14:30:12 +0200] [Job 10] PDF template file doesn't have form. It's okay.
D [08/Aug/2015:14:30:12 +0200] [Job 10] Found device /org/freedesktop/ColorManager/devices/cups_CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Job 10] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [08/Aug/2015:14:30:12 +0200] [Job 10] 'CM Color Calibration' Mode in SPOOLER-LESS: Off
D [08/Aug/2015:14:30:12 +0200] [Job 10] Getting input from file 
D [08/Aug/2015:14:30:12 +0200] [Job 10] foomatic-rip version 1.0.67 running...
D [08/Aug/2015:14:30:12 +0200] [Job 10] Parsing PPD file ...
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option OptCST
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option WideA4
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option PrintDensity
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option ColorSpace
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option InputSlot
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option MediaType
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option Duplex
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option BindingLocation
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option CN_DPI
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option Resolution
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option GSResolution
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option JCLResolution
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option ImageRefine
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option TonerSave
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option ScreenProc
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option Transfer
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option LeadingEdge
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option PageSize
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option ImageableArea
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option PaperDimension
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option Font
D [08/Aug/2015:14:30:12 +0200] [Job 10] Added option ColorSep
D [08/Aug/2015:14:30:12 +0200] [Job 10] Parameter Summary
D [08/Aug/2015:14:30:12 +0200] [Job 10] -----------------
D [08/Aug/2015:14:30:12 +0200] [Job 10] Spooler: cups
D [08/Aug/2015:14:30:12 +0200] [Job 10] Printer: CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Job 10] Shell: /bin/bash
D [08/Aug/2015:14:30:12 +0200] [Job 10] PPD file: /etc/cups/ppd/CanonLBP6670dn.ppd
D [08/Aug/2015:14:30:12 +0200] [Job 10] ATTR file: 
D [08/Aug/2015:14:30:12 +0200] [Job 10] Printer model: Canon LBP6670 PCL
D [08/Aug/2015:14:30:12 +0200] [Job 10] Job title: Test Page
D [08/Aug/2015:14:30:12 +0200] [Job 10] File(s) to be printed:
D [08/Aug/2015:14:30:12 +0200] [Job 10] <STDIN>
D [08/Aug/2015:14:30:12 +0200] [Job 10] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [08/Aug/2015:14:30:12 +0200] [Job 10] Printing system options:
D [08/Aug/2015:14:30:12 +0200] [Job 10] Pondering option 'job-uuid=urn:uuid:9b7bb467-53ee-3a81-430a-c4c85c7df805'
D [08/Aug/2015:14:30:12 +0200] [Job 10] Unknown option job-uuid=urn:uuid:9b7bb467-53ee-3a81-430a-c4c85c7df805.
D [08/Aug/2015:14:30:12 +0200] [Job 10] Pondering option 'job-originating-host-name=localhost'
D [08/Aug/2015:14:30:12 +0200] [Job 10] Unknown option job-originating-host-name=localhost.
D [08/Aug/2015:14:30:12 +0200] [Job 10] Pondering option 'time-at-creation=1439037012'
D [08/Aug/2015:14:30:12 +0200] [Job 10] Unknown option time-at-creation=1439037012.
D [08/Aug/2015:14:30:12 +0200] [Job 10] Pondering option 'time-at-processing=1439037012'
D [08/Aug/2015:14:30:12 +0200] [Job 10] Unknown option time-at-processing=1439037012.
D [08/Aug/2015:14:30:12 +0200] [Job 10] CM Color Calibration Mode in CUPS: Off
D [08/Aug/2015:14:30:12 +0200] [Job 10] Options from the PPD file:
D [08/Aug/2015:14:30:12 +0200] [Job 10] ================================================
D [08/Aug/2015:14:30:12 +0200] [Job 10] File: <STDIN>
D [08/Aug/2015:14:30:12 +0200] [Job 10] ================================================
D [08/Aug/2015:14:30:12 +0200] [Job 10] PID 22567 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [08/Aug/2015:14:30:12 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 39] 2.0 Get-Printer-Attributes 22
D [08/Aug/2015:14:30:12 +0200] Get-Printer-Attributes ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:12 +0200] [Client 39] Returning IPP successful-ok  for Get-Printer-Attributes  (ipp://alain@localhost:631/printers/CanonLBP6670dn) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 39] Content-Length: 188
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:30:12 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=188, response=0x7f5ec0d63910(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 39] bytes=0, http_state=0, data_remaining=188
D [08/Aug/2015:14:30:12 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 38] 2.0 Get-Jobs 21
D [08/Aug/2015:14:30:12 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:30:12 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 38] Content-Length: 867
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=867, response=0x7f5ec0f30cc0(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] bytes=0, http_state=0, data_remaining=867
D [08/Aug/2015:14:30:12 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:12 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:30:12 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:30:12 +0200] [Client 38] 2.0 Get-Jobs 22
D [08/Aug/2015:14:30:12 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:30:12 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:30:12 +0200] [Client 38] Content-Length: 867
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:30:12 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=867, response=0x7f5ec0d63910(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:12 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:12 +0200] [Client 38] bytes=0, http_state=0, data_remaining=867
D [08/Aug/2015:14:30:12 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:30:12 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:12 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:30:12 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:12 +0200] [Job 10] Filetype: PDF
D [08/Aug/2015:14:30:12 +0200] [Job 10] Storing temporary files in /tmp
D [08/Aug/2015:14:30:12 +0200] [Job 10] PID 22568 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [08/Aug/2015:14:30:12 +0200] [Job 10] File contains 2 pages
D [08/Aug/2015:14:30:12 +0200] [Job 10] Starting renderer with command:  gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dPDFFitPage   -sDEVICE=ljet4 -dNOPAUSE  -sPAPERSIZE=a4 -sOutputFile=-      /tmp/foomatic-7eR9EL | sicgsfilter -MPCL -NP  -Q9 -d1 -ualain -V"Test  Page" -n1 
D [08/Aug/2015:14:30:12 +0200] [Job 10] Starting process "kid3" (generation 1)
D [08/Aug/2015:14:30:12 +0200] [Job 10] Starting process "kid4" (generation 2)
D [08/Aug/2015:14:30:12 +0200] [Job 10] Starting process "renderer" (generation 2)
D [08/Aug/2015:14:30:12 +0200] [Job 10] JCL: %-12345X@PJL
D [08/Aug/2015:14:30:12 +0200] [Job 10] <job data> 
D [08/Aug/2015:14:30:12 +0200] [Job 10] /bin/bash: sicgsfilter: command not found
D [08/Aug/2015:14:30:13 +0200] [Job 10] renderer exited with status 127
D [08/Aug/2015:14:30:13 +0200] [Job 10] Kid3 exit status: 1
D [08/Aug/2015:14:30:13 +0200] [Job 10] PID 22569 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9.
D [08/Aug/2015:14:30:16 +0200] [Job 10] prtGeneralCurrentLocalization type is 0, expected 2!
D [08/Aug/2015:14:30:16 +0200] [Job 10] backendWaitLoop(snmp_fd=7, addr=0x7f8049726418, side_cb=0x7f8048a7b060)
D [08/Aug/2015:14:30:16 +0200] [Job 10] PID 22570 (/usr/lib/cups/backend/http) exited with no errors.
D [08/Aug/2015:14:30:16 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
E [08/Aug/2015:14:30:16 +0200] [Job 10] Job stopped due to filter errors; please consult the error_log file for details.
D [08/Aug/2015:14:30:16 +0200] cupsdMarkDirty(---J-)
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [08/Aug/2015:14:30:16 +0200] cupsdMarkDirty(----S)
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [08/Aug/2015:14:30:16 +0200] cupsdMarkDirty(---J-)
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Job 10] The following messages were recorded from 14:30:12 to 14:30:14
D [08/Aug/2015:14:30:16 +0200] [Job 10] op='+', new_reasons=1, state_reasons=1
D [08/Aug/2015:14:30:16 +0200] [Job 10] hrDeviceDesc="Unknown"
D [08/Aug/2015:14:30:16 +0200] [Job 10] End of messages
D [08/Aug/2015:14:30:16 +0200] [Job 10] printer-state=3(idle)
D [08/Aug/2015:14:30:16 +0200] [Job 10] printer-state-message="Filter failed"
D [08/Aug/2015:14:30:16 +0200] [Job 10] printer-state-reasons=none
D [08/Aug/2015:14:30:16 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:16 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:16 +0200] [Notifier] JobState
D [08/Aug/2015:14:30:16 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:16 +0200] [Notifier] state=3
D [08/Aug/2015:14:30:16 +0200] [Client 43] POST / HTTP/1.1
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Printing jobs and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 43] Read: status=200
D [08/Aug/2015:14:30:16 +0200] [Client 43] No authentication data provided.
D [08/Aug/2015:14:30:16 +0200] [Client 43] 2.0 Get-Printer-Attributes 7
D [08/Aug/2015:14:30:16 +0200] Get-Printer-Attributes ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:16 +0200] [Client 43] Returning IPP successful-ok  for Get-Printer-Attributes  (ipp://alain@localhost:631/printers/CanonLBP6670dn) from localhost
D [08/Aug/2015:14:30:16 +0200] [Client 43] Content-Length: 554
D [08/Aug/2015:14:30:16 +0200] [Client 43] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:16 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:30:16 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:30:16 +0200] [Client 39] 2.0 Get-Printer-Attributes 23
D [08/Aug/2015:14:30:16 +0200] Get-Printer-Attributes ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:16 +0200] [Client 39] Returning IPP successful-ok  for Get-Printer-Attributes  (ipp://alain@localhost:631/printers/CanonLBP6670dn) from localhost
D [08/Aug/2015:14:30:16 +0200] [Client 39] Content-Length: 201
D [08/Aug/2015:14:30:16 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:16 +0200] [Client 43] con->http=0x7f5ec0d600e0
D [08/Aug/2015:14:30:16 +0200] [Client 43] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=554, response=0x7f5ec0a38630(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:16 +0200] [Client 43] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:16 +0200] [Client 43] bytes=0, http_state=0, data_remaining=554
D [08/Aug/2015:14:30:16 +0200] [Client 43] Flushing write buffer.
D [08/Aug/2015:14:30:16 +0200] [Client 43] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:16 +0200] [Client 43] Waiting for request.
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:30:16 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=201, response=0x7f5ec0a37750(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:16 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:16 +0200] [Client 39] bytes=0, http_state=0, data_remaining=201
D [08/Aug/2015:14:30:16 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:30:16 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:16 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:30:16 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:30:16 +0200] [Client 38] 2.0 Get-Jobs 23
D [08/Aug/2015:14:30:16 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:30:16 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:30:16 +0200] [Client 38] Content-Length: 899
D [08/Aug/2015:14:30:16 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:16 +0200] [Client 39] POST / HTTP/1.1
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 39] Read: status=200
D [08/Aug/2015:14:30:16 +0200] [Client 39] No authentication data provided.
D [08/Aug/2015:14:30:16 +0200] [Client 39] 2.0 Get-Jobs 24
D [08/Aug/2015:14:30:16 +0200] Get-Jobs ipp://alain@localhost:631/printers/CanonLBP6670dn
D [08/Aug/2015:14:30:16 +0200] [Client 39] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/CanonLBP6670dn) from  localhost
D [08/Aug/2015:14:30:16 +0200] [Client 39] Content-Length: 899
D [08/Aug/2015:14:30:16 +0200] [Client 39] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:16 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:30:16 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=899, response=0x7f5ec0a38630(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:16 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:16 +0200] [Client 38] bytes=0, http_state=0, data_remaining=899
D [08/Aug/2015:14:30:16 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:30:16 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:16 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active  clients and dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 39] con->http=0x7f5ec0d5ced0
D [08/Aug/2015:14:30:16 +0200] [Client 39] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=899, response=0x7f5ec0a3a800(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:16 +0200] [Client 39] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:16 +0200] [Client 39] bytes=0, http_state=0, data_remaining=899
D [08/Aug/2015:14:30:16 +0200] [Client 39] Flushing write buffer.
D [08/Aug/2015:14:30:16 +0200] [Client 39] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:16 +0200] [Client 39] Waiting for request.
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 38] POST / HTTP/1.1
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [08/Aug/2015:14:30:16 +0200] [Client 38] Read: status=200
D [08/Aug/2015:14:30:16 +0200] [Client 38] No authentication data provided.
D [08/Aug/2015:14:30:16 +0200] [Client 38] 2.0 Get-Jobs 24
D [08/Aug/2015:14:30:16 +0200] Get-Jobs ipp://alain@localhost:631/printers/
D [08/Aug/2015:14:30:16 +0200] [Client 38] Returning IPP successful-ok  for Get-Jobs (ipp://alain@localhost:631/printers/) from localhost
D [08/Aug/2015:14:30:16 +0200] [Client 38] Content-Length: 899
D [08/Aug/2015:14:30:16 +0200] [Client 38] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [08/Aug/2015:14:30:16 +0200] [Client 38] con->http=0x7f5ec10d3b80
D [08/Aug/2015:14:30:16 +0200] [Client 38] cupsdWriteClient error=0,  used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH,  data_remaining=899, response=0x7f5ec0a39180(IPP_STATE_DATA), pipe_pid=0,  file=-1
D [08/Aug/2015:14:30:16 +0200] [Client 38] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [08/Aug/2015:14:30:16 +0200] [Client 38] bytes=0, http_state=0, data_remaining=899
D [08/Aug/2015:14:30:16 +0200] [Client 38] Flushing write buffer.
D [08/Aug/2015:14:30:16 +0200] [Client 38] New state is HTTP_STATE_WAITING
D [08/Aug/2015:14:30:16 +0200] [Client 38] Waiting for request.
D [08/Aug/2015:14:30:16 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [08/Aug/2015:14:30:17 +0200] [Job 10] Unloading...
I [08/Aug/2015:14:30:23 +0200] Generating printcap /var/run/cups/printcap...
I [08/Aug/2015:14:30:23 +0200] Saving job.cache...
I [08/Aug/2015:14:30:23 +0200] Saving subscriptions.conf...
D [08/Aug/2015:14:30:23 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"

[/FONT]

---

### Post by alain.roger on 2015-08-08
ok i finally discovered that a new driver version (v3.00) exists with URF-II and it's works like a charm.

---


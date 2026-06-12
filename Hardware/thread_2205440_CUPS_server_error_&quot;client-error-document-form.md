---
title: "CUPS server error: &quot;client-error-document-format-not-supported&quot;"
date: 2014-02-13
forum: Hardware
---

### Post by pkleiber-hi on 2014-02-13
I'm trying to print on a Canon MX882 from my ubuntu 12.04 system. I've followed advice in relevant threads in this and other forums including Ken's Blog and detailed instructions from Salamanca in a closed thread in this forum. I downloaded and installed drivers from Europe as instructed, and I even re-installed Cups, but whatever I do just leads to the CUPS error above. I must be neglecting something obvious. Would appreciate help in interpreting the log below.   Thanks Pierre

D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:49 -1000] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:23:49 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:23:49 -1000] cupsdReadClient: 15 1.1 Get-Jobs 1
D [13/Feb/2014:14:23:49 -1000] Get-Jobs ipp://localhost/printers/
D [13/Feb/2014:14:23:49 -1000] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:49 -1000] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:23:49 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:23:49 -1000] cupsdReadClient: 15 1.1 Get-Jobs 1
D [13/Feb/2014:14:23:49 -1000] Get-Jobs ipp://localhost/printers/
D [13/Feb/2014:14:23:49 -1000] [Job 212] Loading attributes...
D [13/Feb/2014:14:23:49 -1000] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:49 -1000] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:23:49 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:23:49 -1000] cupsdReadClient: 15 1.1 Create-Printer-Subscription 1
D [13/Feb/2014:14:23:49 -1000] Create-Printer-Subscription /
D [13/Feb/2014:14:23:49 -1000] cupsdCreateSubscription(con=0x7fec5d681810(15), uri="/")
D [13/Feb/2014:14:23:49 -1000] pullmethod="ippget"
D [13/Feb/2014:14:23:49 -1000] notify-lease-duration=86400
D [13/Feb/2014:14:23:49 -1000] notify-time-interval=0
D [13/Feb/2014:14:23:49 -1000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [13/Feb/2014:14:23:49 -1000] Added subscription #177 for server.
D [13/Feb/2014:14:23:49 -1000] cupsdMarkDirty(-----S)
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:49 -1000] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [13/Feb/2014:14:23:49 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:50 -1000] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Feb/2014:14:23:50 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:23:50 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:23:50 -1000] cupsdReadClient: 15 1.1 Get-Notifications 1
D [13/Feb/2014:14:23:50 -1000] Get-Notifications /
D [13/Feb/2014:14:23:50 -1000] cupsdIsAuthorized: requesting-user-name="pkleiber"
D [13/Feb/2014:14:23:50 -1000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Feb/2014:14:23:50 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:59 -1000] cupsdAcceptClient: 16 from localhost (Domain)
D [13/Feb/2014:14:23:59 -1000] cupsdReadClient: 16 POST /printers/Canon-MX880-series HTTP/1.1
D [13/Feb/2014:14:23:59 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:23:59 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:23:59 -1000] cupsdReadClient: 16 1.1 Print-Job 1
D [13/Feb/2014:14:23:59 -1000] Print-Job ipp://localhost/printers/Canon-MX880-series
D [13/Feb/2014:14:23:59 -1000] [Job ???] Auto-typing file...
I [13/Feb/2014:14:23:59 -1000] [Job ???] Request file type is application/octet-stream.
D [13/Feb/2014:14:23:59 -1000] Print-Job client-error-document-format-not-supported: Unsupported format "application/octet-stream".
E [13/Feb/2014:14:23:59 -1000] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost/printers/Canon-MX880-series) from localhost
D [13/Feb/2014:14:23:59 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:23:59 -1000] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Feb/2014:14:23:59 -1000] cupsdReadClient: 17 POST /printers/Canon-MX880-series HTTP/1.1
D [13/Feb/2014:14:23:59 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:23:59 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:23:59 -1000] cupsdReadClient: 17 1.1 Print-Job 1
D [13/Feb/2014:14:23:59 -1000] Print-Job ipp://localhost/printers/Canon-MX880-series
D [13/Feb/2014:14:23:59 -1000] Print-Job client-error-document-format-not-supported: Unsupported document-format "text/plain".
I [13/Feb/2014:14:23:59 -1000] Hint: Do you have the raw file printing rules enabled?
E [13/Feb/2014:14:23:59 -1000] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost/printers/Canon-MX880-series) from localhost
D [13/Feb/2014:14:23:59 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 1.1 Cancel-Subscription 1
D [13/Feb/2014:14:24:09 -1000] Cancel-Subscription /
D [13/Feb/2014:14:24:09 -1000] cupsdIsAuthorized: requesting-user-name="pkleiber"
D [13/Feb/2014:14:24:09 -1000] cupsdMarkDirty(-----S)
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:14:24:09 -1000] cupsdIsAuthorized: username=""
D [13/Feb/2014:14:24:09 -1000] cupsdSendHeader: 15 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [13/Feb/2014:14:24:09 -1000] cupsdCloseClient: 15
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAcceptClient: 15 from localhost (Domain)
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAuthorize: Authorized as pkleiber using PeerCred
D [13/Feb/2014:14:24:09 -1000] cupsdIsAuthorized: username="pkleiber"
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAuthorize: Authorized as pkleiber using PeerCred
D [13/Feb/2014:14:24:09 -1000] cupsdIsAuthorized: username="pkleiber"
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAuthorize: Authorized as pkleiber using PeerCred
D [13/Feb/2014:14:24:09 -1000] cupsdIsAuthorized: username="pkleiber"
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdAuthorize: Authorized as pkleiber using PeerCred
D [13/Feb/2014:14:24:09 -1000] cupsdIsAuthorized: username="pkleiber"
I [13/Feb/2014:14:24:09 -1000] Installing config file "/etc/cups/cupsd.conf"...
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdCloseClient: 16
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdCloseClient: 17
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdCloseClient: 15
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [13/Feb/2014:14:24:09 -1000] cupsdDeregisterPrinter(p=0x7fec5d510c40(Canon-MX880-series), removeit=1)
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "lo" = localhost:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "wlan0" = 192.168.1.106:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "vmnet1" = 192.168.39.1:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "vmnet8" = 172.16.30.1:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "lo" = localhost:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "wlan0" = [v1.fe80::5a91:cfff:fe54:4f8e+wlan0]:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "vmnet1" = [v1.fe80::250:56ff:fec0:1+vmnet1]:631
D [13/Feb/2014:14:24:09 -1000] cupsdNetIFUpdate: "vmnet8" = [v1.fe80::250:56ff:fec0:8+vmnet8]:631
D [13/Feb/2014:14:24:09 -1000] cupsdDeregisterPrinter(p=0x7fec5d4e08c0(PDF), removeit=1)
I [13/Feb/2014:14:24:09 -1000] Saving printers.conf...
I [13/Feb/2014:14:24:09 -1000] Generating printcap /var/run/cups/printcap...
I [13/Feb/2014:14:24:09 -1000] Saving subscriptions.conf...
D [13/Feb/2014:14:24:09 -1000] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [13/Feb/2014:14:24:09 -1000] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [13/Feb/2014:14:24:09 -1000] Unknown directive JobPrivateAccess on line 90 of /etc/cups/cupsd.conf.
E [13/Feb/2014:14:24:09 -1000] Unknown directive JobPrivateValues on line 91 of /etc/cups/cupsd.conf.
E [13/Feb/2014:14:24:09 -1000] Unknown directive SubscriptionPrivateAccess on line 92 of /etc/cups/cupsd.conf.
E [13/Feb/2014:14:24:09 -1000] Unknown directive SubscriptionPrivateValues on line 93 of /etc/cups/cupsd.conf.
W [13/Feb/2014:14:24:10 -1000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MX880-series-Gray..' already exists
W [13/Feb/2014:14:24:10 -1000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MX880-series-RGB..' already exists
W [13/Feb/2014:14:24:10 -1000] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-MX880-series' already exists
E [13/Feb/2014:14:24:10 -1000] Failed to update TXT record for Canon MX880 series @ pkslaptop: -2

---


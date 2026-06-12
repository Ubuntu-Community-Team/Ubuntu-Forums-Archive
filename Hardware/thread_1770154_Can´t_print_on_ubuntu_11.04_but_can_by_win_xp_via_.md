---
title: "Can´t print on ubuntu 11.04 but can by win xp via cups"
date: 2011-05-28
forum: Hardware
---

### Post by Fidias on 2011-05-28
Hello, this is my firts thread, hope that it can be solved!!

i have been using ubuntu for 3 years.. no problem at all.. and any problem was already solved in this forum, but this is a tricky one (hope not)

My notebook is conected to a printer, and im sharing it to other two windows notebooks, using CUPS, there has never been a problem, but some days ago, i couldnt print from my notebook but i can from the other computers, i clicked the option to diagnosis, and the wierd thing is that i can print the cups test page from my pc, but i cant print the other documents. this is the eror code that i have

> D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:15:22 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:15:22 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:15:22 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [28/May/2011:20:15:22 -0400] Get-Jobs ipp://localhost/printers/
D [28/May/2011:20:15:22 -0400] [Job 62] Loading attributes...
D [28/May/2011:20:15:22 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:15:22 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:15:22 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:15:22 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [28/May/2011:20:15:22 -0400] Get-Jobs ipp://localhost/printers/
D [28/May/2011:20:15:22 -0400] [Job 1] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 2] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 3] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 4] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 5] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 6] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 7] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 8] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 9] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 10] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 11] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 12] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 13] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 14] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 15] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 16] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 17] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 18] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 19] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 20] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 21] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 22] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 23] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 24] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 25] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 26] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 27] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 28] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 29] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 30] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 31] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 32] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 33] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 34] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 35] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 36] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 37] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 38] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 39] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 40] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 41] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 42] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 43] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 44] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 45] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 46] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 47] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 48] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 49] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 50] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 51] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 52] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 53] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 54] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 55] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 57] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 58] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 59] Loading attributes...
D [28/May/2011:20:15:22 -0400] [Job 60] Loading attributes...
D [28/May/2011:20:15:22 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:15:22 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:15:22 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:15:22 -0400] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [28/May/2011:20:15:22 -0400] Create-Printer-Subscription /
D [28/May/2011:20:15:22 -0400] cupsdCreateSubscription(con=0x2165da20(12), uri="/")
D [28/May/2011:20:15:22 -0400] pullmethod="ippget"
D [28/May/2011:20:15:22 -0400] notify-lease-duration=86400
D [28/May/2011:20:15:22 -0400] notify-time-interval=0
D [28/May/2011:20:15:22 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [28/May/2011:20:15:22 -0400] Added subscription 179 for server
D [28/May/2011:20:15:22 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:15:22 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [28/May/2011:20:15:22 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:15:23 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:15:23 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:15:23 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:15:23 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:15:23 -0400] Get-Notifications /
D [28/May/2011:20:15:23 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:15:23 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:15:23 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:15:48 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:15:48 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:15:48 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:15:48 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:15:48 -0400] Report: clients=9
D [28/May/2011:20:15:48 -0400] Report: jobs=62
D [28/May/2011:20:15:48 -0400] Report: jobs-active=1
D [28/May/2011:20:15:48 -0400] Report: printers=1
D [28/May/2011:20:15:48 -0400] Report: printers-implicit=0
D [28/May/2011:20:15:48 -0400] Report: stringpool-string-count=7825
D [28/May/2011:20:15:48 -0400] Report: stringpool-alloc-bytes=15144
D [28/May/2011:20:15:48 -0400] Report: stringpool-total-bytes=154200
I [28/May/2011:20:15:53 -0400] Saving subscriptions.conf...
D [28/May/2011:20:15:53 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:23 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:16:23 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:23 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:16:23 -0400] [Job 1] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 2] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 3] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 4] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 5] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 6] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 7] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 8] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 9] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 10] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 11] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 12] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 13] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 14] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 15] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 16] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 17] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 18] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 19] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 20] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 21] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 22] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 23] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 24] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 25] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 26] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 27] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 28] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 29] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 30] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 31] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 32] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 33] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 34] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 35] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 36] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 37] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 38] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 39] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 40] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 41] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 42] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 43] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 44] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 45] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 46] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 47] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 48] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 49] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 50] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 51] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 52] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 53] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 54] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 55] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 56] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 57] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 58] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 59] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 60] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 61] Unloading...
D [28/May/2011:20:16:23 -0400] [Job 62] Unloading...
D [28/May/2011:20:16:23 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:16:23 -0400] Get-Notifications /
D [28/May/2011:20:16:23 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:16:23 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:23 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:40 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:40 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:40 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:40 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:40 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:40 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:40 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:40 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:40 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:40 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:40 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 GET /printers/DESKJET-810C.ppd HTTP/1.1
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:41 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:41 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:41 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:41 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:41 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:41 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:41 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:41 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:41 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:41 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:41 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:41 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:41 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:41 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:41 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:41 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:41 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:41 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:41 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:42 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:42 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:42 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:42 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:42 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:42 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:42 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:42 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:42 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:42 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:42 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:42 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:42 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:42 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:42 -0400] cupsdReadClient: 24 1.1 CUPS-Get-Printers 1
D [28/May/2011:20:16:42 -0400] CUPS-Get-Printers
D [28/May/2011:20:16:42 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [28/May/2011:20:16:42 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:16:43 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:43 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:43 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:43 -0400] cupsdReadClient: 23 POST /printers/DESKJET-810C HTTP/1.1
D [28/May/2011:20:16:43 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:16:43 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:43 -0400] cupsdReadClient: 23 1.1 Print-Job 1
D [28/May/2011:20:16:43 -0400] Print-Job ipp://localhost:631/printers/DESKJET-810C
D [28/May/2011:20:16:43 -0400] [Job ???] Auto-typing file...
I [28/May/2011:20:16:43 -0400] [Job ???] Request file type is application/pdf.
D [28/May/2011:20:16:43 -0400] cupsdMarkDirty(----J-)
D [28/May/2011:20:16:43 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:43 -0400] add_job: requesting-user-name="fidias"
I [28/May/2011:20:16:43 -0400] [Job 63] Adding start banner page "none".
D [28/May/2011:20:16:43 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:43 -0400] cupsdMarkDirty(----J-)
I [28/May/2011:20:16:43 -0400] [Job 63] Adding end banner page "none".
I [28/May/2011:20:16:43 -0400] [Job 63] File of type application/pdf queued by "fidias".
D [28/May/2011:20:16:43 -0400] [Job 63] hold_until=0
I [28/May/2011:20:16:43 -0400] [Job 63] Queued on "DESKJET-810C" by "fidias".
D [28/May/2011:20:16:43 -0400] cupsdMarkDirty(----J-)
D [28/May/2011:20:16:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:43 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:43 -0400] [Job 63] job-sheets=none,none
D [28/May/2011:20:16:43 -0400] [Job 63] argv[0]="DESKJET-810C"
D [28/May/2011:20:16:43 -0400] [Job 63] argv[1]="63"
D [28/May/2011:20:16:43 -0400] [Job 63] argv[2]="fidias"
D [28/May/2011:20:16:43 -0400] [Job 63] argv[3]="LABdosS12011"
D [28/May/2011:20:16:43 -0400] [Job 63] argv[4]="1"
D [28/May/2011:20:16:43 -0400] [Job 63] argv[5]="InputSlot=Auto number-up=1 PageSize=Letter MediaType=Plain OutputMode=NormalGray job-uuid=urn:uuid:8398dc25-0a0f-358e-7422-2a2de0612bfb job-originating-host-name=localhost time-at-creation=1306628203 time-at-processing=1306628203"
D [28/May/2011:20:16:43 -0400] [Job 63] argv[6]="/var/spool/cups/d00063-001"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[8]="HOME=/var/spool/cups/tmp"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[10]="SERVER_ADMIN=root@fidias-laptop"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[11]="SOFTWARE=CUPS/1.4.6"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[13]="USER=root"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[16]="IPP_PORT=631"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[17]="CHARSET=utf-8"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[18]="LANG=es_CL.UTF-8"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[19]="PPD=/etc/cups/ppd/DESKJET-810C.ppd"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[20]="RIP_MAX_CACHE=auto"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[21]="CONTENT_TYPE=application/pdf"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[22]="DEVICE_URI=hp:/usb/DeskJet_810C?serial=MX9941T0P0FY"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[23]="PRINTER_INFO=HEWLETT-PACKARD DESKJET 810C"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[24]="PRINTER_LOCATION=fidias-laptop"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[25]="PRINTER=DESKJET-810C"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[26]="CUPS_FILETYPE=document"
D [28/May/2011:20:16:43 -0400] [Job 63] envp[27]="FINAL_CONTENT_TYPE=printer/DESKJET-810C"
I [28/May/2011:20:16:43 -0400] [Job 63] Started filter /usr/lib/cups/filter/pdftopdf (PID 6455)
I [28/May/2011:20:16:43 -0400] [Job 63] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 6456)
I [28/May/2011:20:16:43 -0400] [Job 63] Started filter /usr/lib/cups/filter/hpcups (PID 6457)
I [28/May/2011:20:16:43 -0400] [Job 63] Started backend /usr/lib/cups/backend/hp (PID 6458)
D [28/May/2011:20:16:43 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:43 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/DESKJET-810C) from localhost
D [28/May/2011:20:16:43 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:43 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:43 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:43 -0400] [Job 63] mediaBox = [ 0.000000 0.000000 611.999983 791.999983 ]
D [28/May/2011:20:16:43 -0400] [Job 63] size = Letter
D [28/May/2011:20:16:43 -0400] PID 6455 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [28/May/2011:20:16:44 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 1.1 Get-Notifications 1
D [28/May/2011:20:16:44 -0400] Get-Notifications /
D [28/May/2011:20:16:44 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:44 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAcceptClient: 25 from localhost (Domain)
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:44 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 WAITING Closing on EOF
D [28/May/2011:20:16:44 -0400] cupsdCloseClient: 25
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:16:44 -0400] Get-Notifications /
D [28/May/2011:20:16:44 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAcceptClient: 25 from localhost (Domain)
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:44 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 WAITING Closing on EOF
D [28/May/2011:20:16:44 -0400] cupsdCloseClient: 25
D [28/May/2011:20:16:44 -0400] cupsdAcceptClient: 25 from localhost (Domain)
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:44 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 25 WAITING Closing on EOF
D [28/May/2011:20:16:44 -0400] cupsdCloseClient: 25
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:44 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:44 -0400] [Job 63] STATE: +connecting-to-device
D [28/May/2011:20:16:44 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:44 -0400] PID 6457 (/usr/lib/cups/filter/hpcups) stopped with status 1!
D [28/May/2011:20:16:44 -0400] PID 6456 (/usr/lib/cups/filter/pdftoraster-poppler) did not catch or ignore signal 13.
D [28/May/2011:20:16:44 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 23 1.1 Get-Notifications 1
D [28/May/2011:20:16:44 -0400] Get-Notifications /
D [28/May/2011:20:16:44 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:44 -0400] [Job 63] prnt/hpcups/Pcl3Gui.cpp 75: Requested resolution not supported with requested printmodeprnt/hpcups/HPCupsFilter.cpp 420: m_Job initialization failed with error = 25STATE: -connecting-to-device
D [28/May/2011:20:16:44 -0400] [Job 63] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:44 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:16:44 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:16:44 -0400] Get-Notifications /
D [28/May/2011:20:16:44 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:16:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:44 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:45 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:45 -0400] cupsdCloseClient: 23
I [28/May/2011:20:16:52 -0400] [Job 63] ready to print
D [28/May/2011:20:16:52 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:52 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:52 -0400] Report: clients=9
D [28/May/2011:20:16:52 -0400] Report: jobs=63
D [28/May/2011:20:16:52 -0400] Report: jobs-active=2
D [28/May/2011:20:16:52 -0400] Report: printers=1
D [28/May/2011:20:16:52 -0400] Report: printers-implicit=0
D [28/May/2011:20:16:52 -0400] Report: stringpool-string-count=5814
D [28/May/2011:20:16:52 -0400] Report: stringpool-alloc-bytes=10544
D [28/May/2011:20:16:52 -0400] Report: stringpool-total-bytes=111840
D [28/May/2011:20:16:52 -0400] PID 6458 (/usr/lib/cups/backend/hp) exited with no errors.
D [28/May/2011:20:16:52 -0400] cupsdMarkDirty(-----S)
E [28/May/2011:20:16:52 -0400] [Job 63] Job stopped due to filter errors; please consult the error_log file for details.
D [28/May/2011:20:16:52 -0400] cupsdMarkDirty(----J-)
D [28/May/2011:20:16:52 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:53 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:53 -0400] [Job 63] Unloading...
D [28/May/2011:20:16:53 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:16:53 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:16:53 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:16:53 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 23 POST / HTTP/1.1
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:53 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 23 1.1 Get-Notifications 1
D [28/May/2011:20:16:53 -0400] Get-Notifications /
D [28/May/2011:20:16:53 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:16:53 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:16:53 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:53 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 24 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:53 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:53 -0400] [Job 63] Loading attributes...
D [28/May/2011:20:16:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:53 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:53 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:16:53 -0400] Get-Notifications /
D [28/May/2011:20:16:53 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:16:53 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:16:53 -0400] cupsdAcceptClient: 24 from localhost (Domain)
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 24 POST / HTTP/1.1
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:53 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 24 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:53 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:16:53 -0400] cupsdAcceptClient: 25 from localhost (Domain)
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 25 POST / HTTP/1.1
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:53 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1
D [28/May/2011:20:16:53 -0400] Get-Printer-Attributes ipp://fidias-laptop:631/printers/DESKJET-810C
D [28/May/2011:20:16:53 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://fidias-laptop:631/printers/DESKJET-810C) from localhost
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 25 POST / HTTP/1.1
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:53 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 25 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:53 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:16:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:16:53 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 24 WAITING Closing on EOF
D [28/May/2011:20:16:53 -0400] cupsdCloseClient: 24
D [28/May/2011:20:16:53 -0400] cupsdReadClient: 23 WAITING Closing on EOF
D [28/May/2011:20:16:53 -0400] cupsdCloseClient: 23
D [28/May/2011:20:16:58 -0400] cupsdAcceptClient: 23 from localhost (Domain)
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 23 POST /printers/DESKJET-810C HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 23 1.1 Print-Job 1
D [28/May/2011:20:16:58 -0400] Print-Job ipp://localhost/printers/DESKJET-810C
D [28/May/2011:20:16:58 -0400] [Job ???] Auto-typing file...
I [28/May/2011:20:16:58 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [28/May/2011:20:16:58 -0400] cupsdMarkDirty(----J-)
D [28/May/2011:20:16:58 -0400] add_job: requesting-user-name="fidias"
D [28/May/2011:20:16:58 -0400] Adding default job-sheets values "none,none"...
I [28/May/2011:20:16:58 -0400] [Job 64] Adding start banner page "none".
D [28/May/2011:20:16:58 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:58 -0400] cupsdMarkDirty(----J-)
I [28/May/2011:20:16:58 -0400] [Job 64] Adding end banner page "none".
I [28/May/2011:20:16:58 -0400] [Job 64] File of type application/vnd.cups-banner queued by "fidias".
D [28/May/2011:20:16:58 -0400] [Job 64] hold_until=0
I [28/May/2011:20:16:58 -0400] [Job 64] Queued on "DESKJET-810C" by "fidias".
D [28/May/2011:20:16:58 -0400] cupsdMarkDirty(----J-)
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:58 -0400] [Job 64] job-sheets=none,none
D [28/May/2011:20:16:58 -0400] [Job 64] argv[0]="DESKJET-810C"
D [28/May/2011:20:16:58 -0400] [Job 64] argv[1]="64"
D [28/May/2011:20:16:58 -0400] [Job 64] argv[2]="fidias"
D [28/May/2011:20:16:58 -0400] [Job 64] argv[3]="Test Page"
D [28/May/2011:20:16:58 -0400] [Job 64] argv[4]="1"
D [28/May/2011:20:16:58 -0400] [Job 64] argv[5]="job-uuid=urn:uuid:be67429c-8be8-3f4d-71e2-4be6edb8a2fb job-originating-host-name=localhost time-at-creation=1306628218 time-at-processing=1306628218 AP_D_InputSlot="
D [28/May/2011:20:16:58 -0400] [Job 64] argv[6]="/var/spool/cups/d00064-001"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[8]="HOME=/var/spool/cups/tmp"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[10]="SERVER_ADMIN=root@fidias-laptop"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[11]="SOFTWARE=CUPS/1.4.6"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[13]="USER=root"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[16]="IPP_PORT=631"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[17]="CHARSET=utf-8"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[18]="LANG=es_CL.UTF-8"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[19]="PPD=/etc/cups/ppd/DESKJET-810C.ppd"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[20]="RIP_MAX_CACHE=auto"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[22]="DEVICE_URI=hp:/usb/DeskJet_810C?serial=MX9941T0P0FY"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[23]="PRINTER_INFO=HEWLETT-PACKARD DESKJET 810C"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[24]="PRINTER_LOCATION=fidias-laptop"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[25]="PRINTER=DESKJET-810C"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[26]="CUPS_FILETYPE=document"
D [28/May/2011:20:16:58 -0400] [Job 64] envp[27]="FINAL_CONTENT_TYPE=printer/DESKJET-810C"
I [28/May/2011:20:16:58 -0400] [Job 64] Started filter /usr/lib/cups/filter/bannertops (PID 6469)
I [28/May/2011:20:16:58 -0400] [Job 64] Started filter /usr/lib/cups/filter/pstopdf (PID 6470)
I [28/May/2011:20:16:58 -0400] [Job 64] Started filter /usr/lib/cups/filter/pdftopdf (PID 6471)
I [28/May/2011:20:16:58 -0400] [Job 64] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 6472)
I [28/May/2011:20:16:58 -0400] [Job 64] Started filter /usr/lib/cups/filter/hpcups (PID 6473)
I [28/May/2011:20:16:58 -0400] [Job 64] Started backend /usr/lib/cups/backend/hp (PID 6474)
D [28/May/2011:20:16:58 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/DESKJET-810C) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] [Job 64] load_banner(filename="/var/spool/cups/d00064-001")
D [28/May/2011:20:16:58 -0400] [Job 64] pstopdf 5 args: 64 fidias Test Page 1 job-uuid=urn:uuid:be67429c-8be8-3f4d-71e2-4be6edb8a2fb job-originating-host-name=localhost time-at-creation=1306628218 time-at-processing=1306628218 AP_D_InputSlot=
D [28/May/2011:20:16:58 -0400] [Job 64] PPD: /etc/cups/ppd/DESKJET-810C.ppd
D [28/May/2011:20:16:58 -0400] cupsdAcceptClient: 26 from localhost (Domain)
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 26 POST / HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 26 1.1 Get-Notifications 1
D [28/May/2011:20:16:58 -0400] Get-Notifications /
D [28/May/2011:20:16:58 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 26 POST / HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 26 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:58 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/64) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAcceptClient: 27 from localhost (Domain)
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 POST / HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:58 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/64) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 WAITING Closing on EOF
D [28/May/2011:20:16:58 -0400] cupsdCloseClient: 27
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:16:58 -0400] Get-Notifications /
D [28/May/2011:20:16:58 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] [Job 64] Page = 612x792; 18,36 to 594,783
D [28/May/2011:20:16:58 -0400] cupsdAcceptClient: 27 from localhost (Domain)
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 POST / HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:58 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/64) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 WAITING Closing on EOF
D [28/May/2011:20:16:58 -0400] cupsdCloseClient: 27
D [28/May/2011:20:16:58 -0400] cupsdAcceptClient: 27 from localhost (Domain)
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 POST / HTTP/1.1
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:16:58 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 1.1 Get-Job-Attributes 1
D [28/May/2011:20:16:58 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [28/May/2011:20:16:58 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/64) from localhost
D [28/May/2011:20:16:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 27 WAITING Closing on EOF
D [28/May/2011:20:16:58 -0400] cupsdCloseClient: 27
D [28/May/2011:20:16:58 -0400] cupsdReadClient: 26 WAITING Closing on EOF
D [28/May/2011:20:16:58 -0400] cupsdCloseClient: 26
D [28/May/2011:20:16:58 -0400] [Job 64] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [28/May/2011:20:16:58 -0400] [Job 64] PNG image: 192x128x8, color_type=2 (RGB)
D [28/May/2011:20:16:58 -0400] PID 6469 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [28/May/2011:20:16:58 -0400] [Job 64] Resolution:
D [28/May/2011:20:16:58 -0400] [Job 64] Page size: Letter
D [28/May/2011:20:16:58 -0400] [Job 64] Width: 612, height: 792, absolute margins: 18, 36, 594, 783
D [28/May/2011:20:16:58 -0400] [Job 64] Relative margins: 18, 36, 18, 9
D [28/May/2011:20:16:58 -0400] [Job 64] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [28/May/2011:20:16:58 -0400] [Job 64] PostScript to be injected:
D [28/May/2011:20:16:58 -0400] [Job 64] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [28/May/2011:20:17:01 -0400] PID 6470 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [28/May/2011:20:17:01 -0400] [Job 64] mediaBox = [ 0.000000 0.000000 612.000000 792.000000 ]
D [28/May/2011:20:17:01 -0400] [Job 64] size = Letter
D [28/May/2011:20:17:01 -0400] PID 6471 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [28/May/2011:20:17:01 -0400] [Job 64] STATE: +connecting-to-device
D [28/May/2011:20:17:01 -0400] [Job 64] PAGE: 1 1
D [28/May/2011:20:17:01 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:17:01 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:17:01 -0400] cupsdAcceptClient: 27 from localhost (Domain)
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 27 POST / HTTP/1.1
D [28/May/2011:20:17:01 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:17:01 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 27 1.1 Get-Notifications 1
D [28/May/2011:20:17:01 -0400] Get-Notifications /
D [28/May/2011:20:17:01 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:17:01 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:17:01 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:17:01 -0400] cupsdAcceptClient: 28 from localhost (Domain)
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 28 POST / HTTP/1.1
D [28/May/2011:20:17:01 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:17:01 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 28 1.1 Get-Job-Attributes 1
D [28/May/2011:20:17:01 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [28/May/2011:20:17:01 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/64) from localhost
D [28/May/2011:20:17:01 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 28 WAITING Closing on EOF
D [28/May/2011:20:17:01 -0400] cupsdCloseClient: 28
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:17:01 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:17:01 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:17:01 -0400] Get-Notifications /
D [28/May/2011:20:17:01 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:17:01 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:17:01 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:17:01 -0400] cupsdReadClient: 27 WAITING Closing on EOF
D [28/May/2011:20:17:01 -0400] cupsdCloseClient: 27
D [28/May/2011:20:17:01 -0400] [Job 64] STATE: -connecting-to-device
D [28/May/2011:20:17:01 -0400] [Job 64] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [28/May/2011:20:17:01 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:17:02 -0400] cupsdAcceptClient: 27 from localhost (Domain)
D [28/May/2011:20:17:02 -0400] cupsdReadClient: 27 POST / HTTP/1.1
D [28/May/2011:20:17:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:17:02 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:17:02 -0400] cupsdReadClient: 27 1.1 Get-Notifications 1
D [28/May/2011:20:17:02 -0400] Get-Notifications /
D [28/May/2011:20:17:02 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:17:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:17:02 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:17:02 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:17:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [28/May/2011:20:17:02 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:17:02 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:17:02 -0400] Get-Notifications /
D [28/May/2011:20:17:02 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:17:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:17:02 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:17:02 -0400] cupsdReadClient: 27 WAITING Closing on EOF
D [28/May/2011:20:17:02 -0400] cupsdCloseClient: 27
I [28/May/2011:20:17:14 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [28/May/2011:20:17:14 -0400] Saving subscriptions.conf...
D [28/May/2011:20:17:14 -0400] cupsdSetBusyState: Printing jobs
D [28/May/2011:20:18:01 -0400] [Job 63] Unloading...
D [28/May/2011:20:18:01 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:18:01 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:18:01 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:18:01 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:18:01 -0400] Report: clients=11
D [28/May/2011:20:18:01 -0400] Report: jobs=64
D [28/May/2011:20:18:01 -0400] Report: jobs-active=3
D [28/May/2011:20:18:01 -0400] Report: printers=1
D [28/May/2011:20:18:01 -0400] Report: printers-implicit=0
D [28/May/2011:20:18:01 -0400] Report: stringpool-string-count=6091
D [28/May/2011:20:18:01 -0400] Report: stringpool-alloc-bytes=10496
D [28/May/2011:20:18:01 -0400] Report: stringpool-total-bytes=117808
D [28/May/2011:20:18:01 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:18:01 -0400] cupsdSetBusyState: Active clients and printing jobs
D [28/May/2011:20:18:01 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:18:01 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:18:01 -0400] Get-Notifications /
D [28/May/2011:20:18:01 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:18:01 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:18:01 -0400] cupsdSetBusyState: Printing jobs
D [28/May/2011:20:18:20 -0400] Closing client 16 after 300 seconds of inactivity...
D [28/May/2011:20:18:20 -0400] cupsdCloseClient: 16
D [28/May/2011:20:18:29 -0400] Closing client 17 after 300 seconds of inactivity...
D [28/May/2011:20:18:29 -0400] cupsdCloseClient: 17
D [28/May/2011:20:19:01 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:19:01 -0400] cupsdSetBusyState: Active clients and printing jobs
D [28/May/2011:20:19:01 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:19:01 -0400] Report: clients=9
D [28/May/2011:20:19:01 -0400] Report: jobs=64
D [28/May/2011:20:19:01 -0400] Report: jobs-active=3
D [28/May/2011:20:19:01 -0400] Report: printers=1
D [28/May/2011:20:19:01 -0400] Report: printers-implicit=0
D [28/May/2011:20:19:01 -0400] Report: stringpool-string-count=6093
D [28/May/2011:20:19:01 -0400] Report: stringpool-alloc-bytes=10496
D [28/May/2011:20:19:01 -0400] Report: stringpool-total-bytes=117840
D [28/May/2011:20:19:01 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:19:01 -0400] Get-Notifications /
D [28/May/2011:20:19:01 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:19:01 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:19:01 -0400] cupsdSetBusyState: Printing jobs
D [28/May/2011:20:19:03 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:19:03 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:19:03 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:19:03 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:19:05 -0400] PID 6472 (/usr/lib/cups/filter/pdftoraster-poppler) exited with no errors.
D [28/May/2011:20:19:09 -0400] PID 6473 (/usr/lib/cups/filter/hpcups) exited with no errors.
I [28/May/2011:20:19:30 -0400] [Job 64] ready to print
D [28/May/2011:20:19:30 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:19:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [28/May/2011:20:19:30 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:19:31 -0400] PID 6474 (/usr/lib/cups/backend/hp) exited with no errors.
D [28/May/2011:20:19:31 -0400] cupsdMarkDirty(-----S)
I [28/May/2011:20:19:31 -0400] [Job 64] Job completed.
D [28/May/2011:20:19:31 -0400] cupsdMarkDirty(----J-)
D [28/May/2011:20:19:31 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:19:31 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:19:31 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [28/May/2011:20:19:31 -0400] Get-Notifications /
D [28/May/2011:20:19:31 -0400] cupsdIsAuthorized: requesting-user-name="fidias"
D [28/May/2011:20:19:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:19:31 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:19:31 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [28/May/2011:20:19:31 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [28/May/2011:20:19:31 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/64) from localhost
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [28/May/2011:20:19:31 -0400] cupsdCloseClient: 17
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:19:31 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:19:31 -0400] Get-Notifications /
D [28/May/2011:20:19:31 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:19:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:19:31 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:19:31 -0400] cupsdAuthorize: No authentication data provided.
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [28/May/2011:20:19:31 -0400] Get-Printer-Attributes ipp://fidias-laptop:631/printers/DESKJET-810C
D [28/May/2011:20:19:31 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://fidias-laptop:631/printers/DESKJET-810C) from localhost
D [28/May/2011:20:19:31 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:19:31 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [28/May/2011:20:19:31 -0400] cupsdCloseClient: 16
D [28/May/2011:20:19:46 -0400] Closing client 18 after 300 seconds of inactivity...
D [28/May/2011:20:19:46 -0400] cupsdCloseClient: 18
E [28/May/2011:20:19:46 -0400] [Job 62] Stopping unresponsive job!
D [28/May/2011:20:19:54 -0400] Closing client 15 after 300 seconds of inactivity...
D [28/May/2011:20:19:54 -0400] cupsdCloseClient: 15
D [28/May/2011:20:19:54 -0400] Closing client 19 after 300 seconds of inactivity...
D [28/May/2011:20:19:54 -0400] cupsdCloseClient: 19
D [28/May/2011:20:19:54 -0400] Closing client 20 after 300 seconds of inactivity...
D [28/May/2011:20:19:54 -0400] cupsdCloseClient: 20
I [28/May/2011:20:20:01 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [28/May/2011:20:20:01 -0400] Saving subscriptions.conf...
D [28/May/2011:20:20:01 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:20:01 -0400] Report: clients=6
D [28/May/2011:20:20:01 -0400] Report: jobs=64
D [28/May/2011:20:20:01 -0400] Report: jobs-active=2
D [28/May/2011:20:20:01 -0400] Report: printers=1
D [28/May/2011:20:20:01 -0400] Report: printers-implicit=0
D [28/May/2011:20:20:01 -0400] Report: stringpool-string-count=6233
D [28/May/2011:20:20:01 -0400] Report: stringpool-alloc-bytes=10560
D [28/May/2011:20:20:01 -0400] Report: stringpool-total-bytes=120768
D [28/May/2011:20:20:03 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:20:03 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:20:03 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:20:03 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:20:07 -0400] Closing client 21 after 300 seconds of inactivity...
D [28/May/2011:20:20:07 -0400] cupsdCloseClient: 21
D [28/May/2011:20:20:22 -0400] Closing client 22 after 300 seconds of inactivity...
D [28/May/2011:20:20:22 -0400] cupsdCloseClient: 22
D [28/May/2011:20:20:31 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:20:31 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:20:31 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:20:31 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:20:31 -0400] Get-Notifications /
D [28/May/2011:20:20:31 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:20:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:20:31 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:20:32 -0400] [Job 64] Unloading...
D [28/May/2011:20:21:05 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:21:05 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:21:05 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:21:05 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:21:05 -0400] Report: clients=4
D [28/May/2011:20:21:05 -0400] Report: jobs=64
D [28/May/2011:20:21:05 -0400] Report: jobs-active=2
D [28/May/2011:20:21:05 -0400] Report: printers=1
D [28/May/2011:20:21:05 -0400] Report: printers-implicit=0
D [28/May/2011:20:21:05 -0400] Report: stringpool-string-count=6198
D [28/May/2011:20:21:05 -0400] Report: stringpool-alloc-bytes=9840
D [28/May/2011:20:21:05 -0400] Report: stringpool-total-bytes=120048
D [28/May/2011:20:21:31 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:21:31 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:21:31 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:21:31 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:21:31 -0400] Get-Notifications /
D [28/May/2011:20:21:31 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:21:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:21:31 -0400] cupsdSetBusyState: Not busy
E [28/May/2011:20:21:53 -0400] [Job 63] Stopping unresponsive job!
D [28/May/2011:20:21:54 -0400] Closing client 25 after 300 seconds of inactivity...
D [28/May/2011:20:21:54 -0400] cupsdCloseClient: 25
D [28/May/2011:20:21:59 -0400] Closing client 23 after 300 seconds of inactivity...
D [28/May/2011:20:21:59 -0400] cupsdCloseClient: 23
D [28/May/2011:20:22:07 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:22:07 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:22:07 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:22:07 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:22:07 -0400] Report: clients=2
D [28/May/2011:20:22:07 -0400] Report: jobs=64
D [28/May/2011:20:22:07 -0400] Report: jobs-active=2
D [28/May/2011:20:22:07 -0400] Report: printers=1
D [28/May/2011:20:22:07 -0400] Report: printers-implicit=0
D [28/May/2011:20:22:07 -0400] Report: stringpool-string-count=6198
D [28/May/2011:20:22:07 -0400] Report: stringpool-alloc-bytes=9840
D [28/May/2011:20:22:07 -0400] Report: stringpool-total-bytes=120048
D [28/May/2011:20:22:31 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:22:31 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:22:31 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:22:31 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:22:31 -0400] Get-Notifications /
D [28/May/2011:20:22:31 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:22:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:22:31 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:23:09 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:23:09 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.0.139:631
D [28/May/2011:20:23:09 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [28/May/2011:20:23:09 -0400] cupsdNetIFUpdate: "wlan0" = [v1.fe80::216:44ff:fea1:e766+wlan0]:631
D [28/May/2011:20:23:09 -0400] Report: clients=2
D [28/May/2011:20:23:09 -0400] Report: jobs=64
D [28/May/2011:20:23:09 -0400] Report: jobs-active=2
D [28/May/2011:20:23:09 -0400] Report: printers=1
D [28/May/2011:20:23:09 -0400] Report: printers-implicit=0
D [28/May/2011:20:23:09 -0400] Report: stringpool-string-count=6198
D [28/May/2011:20:23:09 -0400] Report: stringpool-alloc-bytes=9840
D [28/May/2011:20:23:09 -0400] Report: stringpool-total-bytes=120048
D [28/May/2011:20:23:31 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:23:31 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:23:31 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:23:31 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [28/May/2011:20:23:31 -0400] Get-Notifications /
D [28/May/2011:20:23:31 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:23:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [28/May/2011:20:23:31 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:24:04 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:24:04 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:24:04 -0400] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [28/May/2011:20:24:04 -0400] Get-Job-Attributes ipp://localhost/jobs/62
D [28/May/2011:20:24:04 -0400] [Job 62] Loading attributes...
D [28/May/2011:20:24:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/62) from localhost
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:24:04 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:24:04 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:24:04 -0400] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [28/May/2011:20:24:04 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [28/May/2011:20:24:04 -0400] [Job 63] Loading attributes...
D [28/May/2011:20:24:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/63) from localhost
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Not busy
D [28/May/2011:20:24:04 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Active clients
D [28/May/2011:20:24:04 -0400] cupsdAuthorize: Authorized as fidias using PeerCred
D [28/May/2011:20:24:04 -0400] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [28/May/2011:20:24:04 -0400] Cancel-Subscription /
D [28/May/2011:20:24:04 -0400] cupsdIsAuthorized: username="fidias"
D [28/May/2011:20:24:04 -0400] cupsdMarkDirty(-----S)
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:24:04 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [28/May/2011:20:24:04 -0400] cupsdSetBusyState: Dirty files
D [28/May/2011:20:24:04 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [28/May/2011:20:24:05 -0400] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [28/May/2011:20:24:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [28/May/2011:20:24:05 -0400] cupsdAuthorize: No authentication data provided.  



any idea?.. thanks!

---


---
title: "Samsung 315w bugs"
date: 2010-01-16
forum: Hardware
---

### Post by RINKO on 2010-01-16
I reported a bug for this problem in office.
I was not able to report this bug so I would like to know who to send it to.  In the mean time can anybody make something out of it?  

> D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Dirty files
D [16/Jan/2010:10:02:24 -0500] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Active clients and dirty files
D [16/Jan/2010:10:02:24 -0500] cupsdAuthorize: No authentication data provided.
D [16/Jan/2010:10:02:24 -0500] cupsdReadClient: 13 1.1 Get-Jobs 1
D [16/Jan/2010:10:02:24 -0500] Get-Jobs ipp://localhost/printers/
D [16/Jan/2010:10:02:24 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Dirty files
D [16/Jan/2010:10:02:24 -0500] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Active clients and dirty files
D [16/Jan/2010:10:02:24 -0500] cupsdAuthorize: No authentication data provided.
D [16/Jan/2010:10:02:24 -0500] cupsdReadClient: 13 1.1 Get-Jobs 1
D [16/Jan/2010:10:02:24 -0500] Get-Jobs ipp://localhost/printers/
[B]D [16/Jan/2010:10:02:24 -0500] [Job 2] Loading attributes...
E [16/Jan/2010:10:02:24 -0500] [Job 2] Unable to open job control file "/var/spool/cups/c00002" - No such file or directory!
D [16/Jan/2010:10:02:24 -0500] [Job 3] Loading attributes...
E [16/Jan/2010:10:02:24 -0500] [Job 3] Unable to open job control file "/var/spool/cups/c00003" - No such file or directory!
D [16/Jan/2010:10:02:24 -0500] [Job 4] Loading attributes...
E [16/Jan/2010:10:02:24 -0500] [Job 4] Unable to open job control file "/var/spool/cups/c00004" - No such file or directory!
D [16/Jan/2010:10:02:24 -0500] [Job 5] Loading attributes...
E [16/Jan/2010:10:02:24 -0500] [Job 5] Unable to open job control file "/var/spool/cups/c00005" - No such file or directory!
D [16/Jan/2010:10:02:24 -0500] [Job 7] Loading attributes...
E [16/Jan/2010:10:02:24 -0500] [Job 7] Unable to open job control file "/var/spool/cups/c00007" - No such file or directory![/B]
D [16/Jan/2010:10:02:24 -0500] [Job 12] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 13] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 14] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 15] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 16] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 17] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 18] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 19] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 20] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 21] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 22] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 23] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 24] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 25] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 26] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 27] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 28] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 29] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 30] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] [Job 31] Loading attributes...
D [16/Jan/2010:10:02:24 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Dirty files
D [16/Jan/2010:10:02:24 -0500] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Active clients and dirty files
D [16/Jan/2010:10:02:24 -0500] cupsdAuthorize: No authentication data provided.
D [16/Jan/2010:10:02:24 -0500] cupsdReadClient: 13 1.1 Create-Printer-Subscription 1
D [16/Jan/2010:10:02:24 -0500] Create-Printer-Subscription /
D [16/Jan/2010:10:02:24 -0500] cupsdCreateSubscription(con=0x18f0c28(13), uri="/")
D [16/Jan/2010:10:02:24 -0500] pullmethod="ippget"
D [16/Jan/2010:10:02:24 -0500] notify-lease-duration=86400
D [16/Jan/2010:10:02:24 -0500] notify-time-interval=0
D [16/Jan/2010:10:02:24 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [16/Jan/2010:10:02:24 -0500] Added subscription 40 for server
D [16/Jan/2010:10:02:24 -0500] cupsdMarkDirty(-----S)
D [16/Jan/2010:10:02:24 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [16/Jan/2010:10:02:24 -0500] cupsdSetBusyState: Dirty files
D [16/Jan/2010:10:02:25 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [16/Jan/2010:10:02:25 -0500] cupsdNetIFUpdate: "eth0" = 192.168.1.100:631
D [16/Jan/2010:10:02:25 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [16/Jan/2010:10:02:25 -0500] cupsdNetIFUpdate: "eth0" = fe80::212:3fff:feaa:12d1%eth0:631
D [16/Jan/2010:10:02:25 -0500] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jan/2010:10:02:25 -0500] cupsdSetBusyState: Active clients and dirty files
D [16/Jan/2010:10:02:25 -0500] cupsdAuthorize: No authentication data provided.
D [16/Jan/2010:10:02:25 -0500] cupsdReadClient: 13 1.1 Get-Notifications 1
D [16/Jan/2010:10:02:25 -0500] Get-Notifications /
D [16/Jan/2010:10:02:25 -0500] cupsdIsAuthorized: requesting-user-name="brian"
D [16/Jan/2010:10:02:25 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jan/2010:10:02:25 -0500] cupsdSetBusyState: Dirty files
D [16/Jan/2010:10:02:38 -0500] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jan/2010:10:02:38 -0500] cupsdSetBusyState: Active clients and dirty files
D [16/Jan/2010:10:02:38 -0500] cupsdAuthorize: No authentication data provided.
D [16/Jan/2010:10:02:38 -0500] cupsdReadClient: 13 1.1 Cancel-Subscription 1
D [16/Jan/2010:10:02:38 -0500] Cancel-Subscription /
D [16/Jan/2010:10:02:38 -0500] cupsdIsAuthorized: requesting-user-name="brian"
D [16/Jan/2010:10:02:38 -0500] cupsdMarkDirty(-----S)
D [16/Jan/2010:10:02:38 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [16/Jan/2010:10:02:38 -0500] cupsdSetBusyState: Dirty files
D [16/Jan/2010:10:02:38 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [16/Jan/2010:10:02:38 -0500] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [16/Jan/2010:10:02:38 -0500] cupsdSetBusyState: Active clients and dirty files
D [16/Jan/2010:10:02:38 -0500] cupsdAuthorize: No authentication data provided.
and then there was the bug report that i saved which is pretty long, probably too long to post in here... Who should i send the bug report to?  
INFORMATION ON THE PRINTER:
Model: Samsung CP-315w
Connection: Ethernet to router, shared network printer, cat5e cable
Other: The problem is intermittent, sometimes I can print. Other times the print log reports that the file was printed but I never get the copy.  Also sometimes it says the printer may not be connected.
Other: I've changed the print priority and still end up waiting 1-3 minutes for a page to print.  I haven't been able to change that setting and have it begin printing right after it receives the data. (like it was connected via usb or firewire)

I appreciate any help.  I'll be checking this thread regularly today 1-16-10 b/c i need to do some work for my small business.  
-Brian

---

### Post by RINKO on 2010-01-16
problem solved i didnt install the driver right.  I didnt make the cups correctly.

close this thread please.

---


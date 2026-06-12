---
title: "brother 2240 in lubuntu 13.04"
date: 2013-09-26
forum: Hardware
---

### Post by oakhollow on 2013-09-26
Printer is recognized but test pages off computer are blank. Ran troubleshooter but no success. Printer is brand new and self test was OK. Suggestions?

---

### Post by Bucky Ball on 2013-09-26
*Thread moved to **Hardware**.*

Go here:

[http://welcome.solutions.brother.com/BSC/public/us/us/en/model_top/monolaserpri/hl2240_us_eu.html?reg=us&c=us&lang=en&prod=hl2240_us_eu](http://welcome.solutions.brother.com/BSC/public/us/us/en/model_top/monolaserpri/hl2240_us_eu.html?reg=us&c=us&lang=en&prod=hl2240_us_eu)

Click Linux in the right hand column. Download and install the driver. Reboot. Try again. 

You would get more help if you give more detail. Is this a wireless printer, USB, network? How are you trying to connect with it? If it is recognised but not printing test pages, you don't have the correct driver. You should install drivers then 'Add Printer'. That will then find and install. Or should.

---

### Post by oakhollow on 2013-09-26
It is a USB. I downloaded and extracted the 2 drivers shown. Still blank pages. On installing a driver in lubuntu, not sure if what I did was right. Here's the error log.


D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"D [26/Sep/2013:16:20:53 -0400] [Client 14] POST / HTTP/1.1
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:20:53 -0400] [Client 14] No authentication data provided.
D [26/Sep/2013:16:20:53 -0400] [Client 14] 2.0 Get-Jobs 20
D [26/Sep/2013:16:20:53 -0400] Get-Jobs ipp://localhost/printers/
D [26/Sep/2013:16:20:53 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:20:53 -0400] [Client 14] POST / HTTP/1.1
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:20:53 -0400] [Client 14] No authentication data provided.
D [26/Sep/2013:16:20:53 -0400] [Client 14] 2.0 Get-Jobs 21
D [26/Sep/2013:16:20:53 -0400] Get-Jobs ipp://localhost/printers/
D [26/Sep/2013:16:20:53 -0400] [Job 4] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 5] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 6] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 7] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 8] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 9] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 10] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 11] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 12] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 13] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 14] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 15] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] [Job 16] Loading attributes...
D [26/Sep/2013:16:20:53 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:20:53 -0400] [Client 14] POST / HTTP/1.1
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:20:53 -0400] [Client 14] No authentication data provided.
D [26/Sep/2013:16:20:53 -0400] [Client 14] 2.0 Create-Printer-Subscription 22
D [26/Sep/2013:16:20:53 -0400] Create-Printer-Subscription /
D [26/Sep/2013:16:20:53 -0400] cupsdCreateSubscription(con=0xb9779518(14), uri="/")
D [26/Sep/2013:16:20:53 -0400] pullmethod="ippget"
D [26/Sep/2013:16:20:53 -0400] notify-lease-duration=86400
D [26/Sep/2013:16:20:53 -0400] notify-time-interval=0
D [26/Sep/2013:16:20:53 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [26/Sep/2013:16:20:53 -0400] Added subscription #18 for server.
D [26/Sep/2013:16:20:53 -0400] cupsdMarkDirty(----S)
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:20:53 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [26/Sep/2013:16:20:53 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:20:54 -0400] [Client 14] POST / HTTP/1.1
D [26/Sep/2013:16:20:55 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:20:55 -0400] [Client 14] No authentication data provided.
D [26/Sep/2013:16:20:55 -0400] [Client 14] 2.0 Get-Notifications 23
D [26/Sep/2013:16:20:55 -0400] Get-Notifications /
D [26/Sep/2013:16:20:55 -0400] cupsdIsAuthorized: requesting-user-name="carol"
D [26/Sep/2013:16:20:55 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [26/Sep/2013:16:20:55 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] POST / HTTP/1.1
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] No authentication data provided.
D [26/Sep/2013:16:21:01 -0400] [Client 14] 2.0 Cancel-Subscription 24
D [26/Sep/2013:16:21:01 -0400] Cancel-Subscription /
D [26/Sep/2013:16:21:01 -0400] cupsdIsAuthorized: requesting-user-name="carol"
D [26/Sep/2013:16:21:01 -0400] cupsdMarkDirty(----S)
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] GET /admin/conf/cupsd.conf HTTP/1.1
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] No authentication data provided.
D [26/Sep/2013:16:21:01 -0400] cupsdIsAuthorized: username=""
D [26/Sep/2013:16:21:01 -0400] [Client 14] WWW-Authenticate: Basic realm="CUPS", trc="y"
D [26/Sep/2013:16:21:01 -0400] [Client 14] Closing connection.
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] Accepted from localhost (Domain)
D [26/Sep/2013:16:21:01 -0400] [Client 14] GET /admin/conf/cupsd.conf HTTP/1.1
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] Authorized as carol using PeerCred
D [26/Sep/2013:16:21:01 -0400] cupsdIsAuthorized: username="carol"
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] GET /admin/conf/cupsd.conf HTTP/1.1
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] Authorized as carol using PeerCred
D [26/Sep/2013:16:21:01 -0400] cupsdIsAuthorized: username="carol"
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] GET /admin/conf/cupsd.conf HTTP/1.1
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] Authorized as carol using PeerCred
D [26/Sep/2013:16:21:01 -0400] cupsdIsAuthorized: username="carol"
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] PUT /admin/conf/cupsd.conf HTTP/1.1
D [26/Sep/2013:16:21:01 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [26/Sep/2013:16:21:01 -0400] [Client 14] Authorized as carol using PeerCred
D [26/Sep/2013:16:21:01 -0400] cupsdIsAuthorized: username="carol"
I [26/Sep/2013:16:21:01 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [26/Sep/2013:16:21:02 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [26/Sep/2013:16:21:02 -0400] [Client 14] Closing connection.
D [26/Sep/2013:16:21:02 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [26/Sep/2013:16:21:02 -0400] Generating printcap /var/run/cups/printcap...
I [26/Sep/2013:16:21:02 -0400] Saving subscriptions.conf...
D [26/Sep/2013:16:21:02 -0400] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [26/Sep/2013:16:21:02 -0400] Unknown directive JobPrivateAccess on line 84 of /etc/cups/cupsd.conf.
E [26/Sep/2013:16:21:02 -0400] Unknown directive JobPrivateValues on line 85 of /etc/cups/cupsd.conf.
E [26/Sep/2013:16:21:02 -0400] Unknown directive SubscriptionPrivateAccess on line 86 of /etc/cups/cupsd.conf.
E [26/Sep/2013:16:21:02 -0400] Unknown directive SubscriptionPrivateValues on line 87 of /etc/cups/cupsd.conf.
W [26/Sep/2013:16:21:02 -0400] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Sep/2013:16:21:02 -0400] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
Here is the error log.

---


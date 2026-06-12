---
title: "'Cannot execute filter' Canon MF4370dn not working"
date: 2011-12-22
forum: Hardware
---

### Post by dahouse on 2011-12-22
Hey Folks!

I've a very frustrating problem. I'm trying to get my Canon IMAGECLASS mf4370dn printer to work over my network. I've followed the steps outlined in the following threads, but unfortunately, the printer isn't doing its job.

[http://ubuntuforums.org/showthread.php?t=1051284](http://ubuntuforums.org/showthread.php?t=1051284)
[http://ubuntuforums.org/showthread.php?t=1140724](http://ubuntuforums.org/showthread.php?t=1140724)

The error I keep on getting is the following:
**"Stopping job because the scheduler could not execute a filter"**

I installed the latest version of the linux drivers from the canon site (v2.3) :
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

The installation seems to go well, it detects the printer over the network, but when I go for a test print, I get the above error. When I select diagnose, the printer's state message is 
**'File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory'.**

Here's the error log:
```

D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 POST / HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: No authentication data provided.
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 1.1 Get-Jobs 1
D [22/Dec/2011:13:08:14 -0500] Get-Jobs ipp://localhost/printers/
D [22/Dec/2011:13:08:14 -0500] [Job 16] Loading attributes...
D [22/Dec/2011:13:08:14 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 POST / HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: No authentication data provided.
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 1.1 Get-Jobs 1
D [22/Dec/2011:13:08:14 -0500] Get-Jobs ipp://localhost/printers/
D [22/Dec/2011:13:08:14 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 GET /admin/conf/cupsd.conf HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: No authentication data provided.
D [22/Dec/2011:13:08:14 -0500] cupsdIsAuthorized: username=""
D [22/Dec/2011:13:08:14 -0500] cupsdSendHeader: 19 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [22/Dec/2011:13:08:14 -0500] cupsdCloseClient: 19
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAcceptClient: 19 from localhost (Domain)
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 GET /admin/conf/cupsd.conf HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: Authorized as cd using PeerCred
D [22/Dec/2011:13:08:14 -0500] cupsdIsAuthorized: username="cd"
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 GET /admin/conf/cupsd.conf HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: Authorized as cd using PeerCred
D [22/Dec/2011:13:08:14 -0500] cupsdIsAuthorized: username="cd"
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 GET /admin/conf/cupsd.conf HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: Authorized as cd using PeerCred
D [22/Dec/2011:13:08:14 -0500] cupsdIsAuthorized: username="cd"
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdReadClient: 19 PUT /admin/conf/cupsd.conf HTTP/1.1
D [22/Dec/2011:13:08:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:14 -0500] cupsdAuthorize: Authorized as cd using PeerCred
D [22/Dec/2011:13:08:14 -0500] cupsdIsAuthorized: username="cd"
I [22/Dec/2011:13:08:14 -0500] Installing config file "/etc/cups/cupsd.conf"...
D [22/Dec/2011:13:08:15 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Dec/2011:13:08:15 -0500] cupsdCloseClient: 18
D [22/Dec/2011:13:08:15 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [22/Dec/2011:13:08:15 -0500] cupsdCloseClient: 19
D [22/Dec/2011:13:08:15 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [22/Dec/2011:13:08:15 -0500] Saving printers.conf...
I [22/Dec/2011:13:08:15 -0500] Generating printcap /var/run/cups/printcap...
I [22/Dec/2011:13:08:15 -0500] Saving subscriptions.conf...
D [22/Dec/2011:13:08:15 -0500] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [22/Dec/2011:13:08:15 -0500] Unknown directive JobPrivateAccess on line 88.
E [22/Dec/2011:13:08:15 -0500] Unknown directive JobPrivateValues on line 89.
E [22/Dec/2011:13:08:15 -0500] Unknown directive SubscriptionPrivateAccess on line 90.
E [22/Dec/2011:13:08:15 -0500] Unknown directive SubscriptionPrivateValues on line 91.
E [22/Dec/2011:13:08:15 -0500] Canon-Canon-MF4360-4390-(UFRII-LT): File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory
W [22/Dec/2011:13:08:15 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_Canon_MF4360_4390__UFRII_LT__Gray__' has already been added
```


THANKS!

---


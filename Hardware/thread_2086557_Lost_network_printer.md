---
title: "Lost network printer"
date: 2012-11-21
forum: Hardware
---

### Post by Lloydb39 on 2012-11-21
I'm using Ubuntu 12.04 on a network and print to an Epson CX4480 attached to a Windows computer. Has been working fine but now when I sent a document to print, nothing happens. Have removed and installed printer a couple of time to no avail. How would I diagnose/fix the problem?
Here is the output of the debug if it means anything to anyone:
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: No authentication data provided.
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 1.1 Get-Jobs 1
D [21/Nov/2012:08:33:14 -0500] Get-Jobs ipp://localhost/printers/
D [21/Nov/2012:08:33:14 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: No authentication data provided.
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 1.1 Get-Jobs 1
D [21/Nov/2012:08:33:14 -0500] Get-Jobs ipp://localhost/printers/
D [21/Nov/2012:08:33:14 -0500] [Job 24] Loading attributes...
D [21/Nov/2012:08:33:14 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 GET /admin/conf/cupsd.conf HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: No authentication data provided.
D [21/Nov/2012:08:33:14 -0500] cupsdIsAuthorized: username=""
D [21/Nov/2012:08:33:14 -0500] cupsdSendHeader: 16 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [21/Nov/2012:08:33:14 -0500] cupsdCloseClient: 16
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 GET /admin/conf/cupsd.conf HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: Authorized as lloyd using PeerCred
D [21/Nov/2012:08:33:14 -0500] cupsdIsAuthorized: username="lloyd"
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 GET /admin/conf/cupsd.conf HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: Authorized as lloyd using PeerCred
D [21/Nov/2012:08:33:14 -0500] cupsdIsAuthorized: username="lloyd"
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 GET /admin/conf/cupsd.conf HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: Authorized as lloyd using PeerCred
D [21/Nov/2012:08:33:14 -0500] cupsdIsAuthorized: username="lloyd"
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdReadClient: 16 PUT /admin/conf/cupsd.conf HTTP/1.1
D [21/Nov/2012:08:33:14 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:14 -0500] cupsdAuthorize: Authorized as lloyd using PeerCred
D [21/Nov/2012:08:33:14 -0500] cupsdIsAuthorized: username="lloyd"
I [21/Nov/2012:08:33:14 -0500] Installing config file "/etc/cups/cupsd.conf"...
D [21/Nov/2012:08:33:15 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [21/Nov/2012:08:33:15 -0500] cupsdCloseClient: 16
D [21/Nov/2012:08:33:15 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [21/Nov/2012:08:33:15 -0500] cupsdDeregisterPrinter(p=0x7f874fd22ab0(EPSON-Stylus-CX4800-Series), removeit=1)
I [21/Nov/2012:08:33:15 -0500] Generating printcap /var/run/cups/printcap...
D [21/Nov/2012:08:33:15 -0500] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
W [21/Nov/2012:08:33:15 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus-CX4800-Series-Gray..' already exists
W [21/Nov/2012:08:33:15 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus-CX4800-Series-RGB..' already exists
W [21/Nov/2012:08:33:15 -0500] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-EPSON-Stylus-CX4800-Series' already exists
E [21/Nov/2012:08:33:15 -0500] Failed to update TXT record for EPSON Stylus CX4800 Series @ lloyd-linux: -2

---


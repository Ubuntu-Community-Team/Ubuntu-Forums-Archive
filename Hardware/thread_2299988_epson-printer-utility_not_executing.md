---
title: "epson-printer-utility not executing"
date: 2015-10-22
forum: Hardware
---

### Post by cscj01 on 2015-10-22
I have Ubuntu 14.04.3 x64 and have just installed an Epson Artisan 1430.  The printer is connected via USB to my PC.  Epson has a package called epson-printer-utility_1.0.0-1lsb3.2_amd64.deb that I have installed.  I cannot get it to execute.  There seem to multiple executables for this program (/usr/bin and /opt/epson-printer-utility/bin), but if I try to launch them from the icon nothing happens.  I have tried to execute both instances of the program from a termiinal, but each one gives me the error> Communication daemon down, Error code = -1
My CUPS error log has the following```
W [22/Oct/2015:07:51:25 -0400] No limit for Validate-Job defined in policy default and no suitable template found.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateAccess defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateValues defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateValues defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateAccess defined in policy authenticated - using defaults.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateValues defined in policy authenticated - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
E [22/Oct/2015:12:02:24 -0400] [Client 18] Request for non-absolute resource "".
E [22/Oct/2015:12:02:24 -0400] [Client 18] Request for non-absolute resource "".
W [22/Oct/2015:12:02:25 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-Gray..' already exists
W [22/Oct/2015:12:02:25 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-RGB..' already exists
E [22/Oct/2015:12:05:00 -0400] [Client 18] Request for non-absolute resource "".
W [22/Oct/2015:12:05:00 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-Gray..' already exists
W [22/Oct/2015:12:05:00 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-RGB..' already exists
W [22/Oct/2015:12:13:45 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-Gray..' already exists
W [22/Oct/2015:12:13:45 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-RGB..' already exists
E [22/Oct/2015:12:24:56 -0400] [Client 19] Request for non-absolute resource "".
W [22/Oct/2015:12:25:05 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-Gray..' already exists
W [22/Oct/2015:12:25:05 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-RGB..' already exists
E [22/Oct/2015:12:25:34 -0400] [Client 19] Disallowed PUT request for "/admin/conf/lpoptions".
E [22/Oct/2015:12:25:34 -0400] [Client 18] Disallowed PUT request for "/admin/conf/lpoptions".W [22/Oct/2015:07:51:25 -0400] No limit for Validate-Job defined in policy default and no suitable template found.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateAccess defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateValues defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateValues defined in policy default - using defaults.
W [22/Oct/2015:07:51:25 -0400] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateAccess defined in policy authenticated - using defaults.
W [22/Oct/2015:07:51:25 -0400] No JobPrivateValues defined in policy authenticated - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [22/Oct/2015:07:51:25 -0400] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
E [22/Oct/2015:12:02:24 -0400] [Client 18] Request for non-absolute resource "".
E [22/Oct/2015:12:02:24 -0400] [Client 18] Request for non-absolute resource "".
W [22/Oct/2015:12:02:25 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-Gray..' already exists
W [22/Oct/2015:12:02:25 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-RGB..' already exists
E [22/Oct/2015:12:05:00 -0400] [Client 18] Request for non-absolute resource "".
W [22/Oct/2015:12:05:00 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-Gray..' already exists
W [22/Oct/2015:12:05:00 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-RGB..' already exists
W [22/Oct/2015:12:13:45 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-Gray..' already exists
W [22/Oct/2015:12:13:45 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Artisan-1430-RGB..' already exists
E [22/Oct/2015:12:24:56 -0400] [Client 19] Request for non-absolute resource "".
W [22/Oct/2015:12:25:05 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-Gray..' already exists
W [22/Oct/2015:12:25:05 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-RGB..' already exists
E [22/Oct/2015:12:25:34 -0400] [Client 19] Disallowed PUT request for "/admin/conf/lpoptions".
E [22/Oct/2015:12:25:34 -0400] [Client 18] Disallowed PUT request for "/admin/conf/lpoptions".
E [22/Oct/2015:12:25:34 -0400] [Client 18] Disallowed PUT request for "/admin/conf/lpoptions".
E [22/Oct/2015:12:25:34 -0400] [Client 20] Disallowed PUT request for "/admin/conf/lpoptions".
W [22/Oct/2015:19:53:28 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-Gray..' already exists
W [22/Oct/2015:19:53:28 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-RGB..' already exists
E [22/Oct/2015:12:25:34 -0400] [Client 18] Disallowed PUT request for "/admin/conf/lpoptions".
E [22/Oct/2015:12:25:34 -0400] [Client 20] Disallowed PUT request for "/admin/conf/lpoptions".
W [22/Oct/2015:19:53:28 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-Gray..' already exists
W [22/Oct/2015:19:53:28 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_Artisan_1430-RGB..' already exists
```From Cups, my driver is > Driver:	Epson Artisan 1430 - epson-inkjet-printer-escpr 1.6.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2) (color, 2-sided printing)and my connection is ```
Connection:	usb://EPSON/Artisan%201430?serial=4E414D593038313832
```I downloaded the utility from here```
http://download.ebz.epson.net/dsc/search/01/search/searchModule
```Even though they don't say anything specific about Ubuntu, the program is available as a .deb, so I'm not sure why it won't run under Ubuntu.  Hopefully someone can help me here, because mtink doesn't seem to be working at all for me.  I can run it, but the ink quantities are all wrong and none of the other functions do anything that I can tell except preferences and exit.

---

### Post by cscj01 on 2015-10-23
I solved this by installing escputil```
sudo apt-get install escputil
```.  I also added usblp to my /etc/modules file.

---


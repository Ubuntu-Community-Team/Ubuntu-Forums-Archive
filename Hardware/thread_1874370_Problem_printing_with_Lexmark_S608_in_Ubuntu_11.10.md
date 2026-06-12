---
title: "Problem printing with Lexmark S608 in Ubuntu 11.10 x64"
date: 2011-11-02
forum: Hardware
---

### Post by jbejr on 2011-11-02
Hello everybody!

I really need some help! I have a Lexmark S608 Printer, which worked fine on Ubuntu 11.04 (at least the printing part).

But after I upgraded to Ubuntu 11.10 I can't print anymore. I tried reinstalling the drivers from Lexmark website but no luck! Tried to contact their support but, up to now, no response. Each day I understand more Richard Stallman...

The funny part is that the scanner, which did not work on Ubuntu 11.04, is now working perfectly!

I know the problem is not with the printer since I can print normally from another OS (it sucks!).

The system adds the printer ok, but when I try to print it stays stopped for a while and then a message box comes up:

"Printer error"

"There was a problem on processing the document "(name of the document)" (job XXX)."

There is a diagnose button. When pressed it gives the following output:

"There are status messages associated with this file.

The state message of the printer is: "(null)"."

I also receive the following messages from cups (from the debugger):

D [03/Nov/2011:01:23:53 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:53 -0200] cupsdReadClient: 14 POST / HTTP/1.1
D [03/Nov/2011:01:23:53 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:53 -0200] cupsdAuthorize: No authentication data provided.
D [03/Nov/2011:01:23:53 -0200] cupsdReadClient: 14 1.1 Get-Jobs 1
D [03/Nov/2011:01:23:53 -0200] Get-Jobs ipp://localhost/printers/
D [03/Nov/2011:01:23:53 -0200] [Job 77] Loading attributes...
D [03/Nov/2011:01:23:53 -0200] [Job 78] Loading attributes...
D [03/Nov/2011:01:23:53 -0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Nov/2011:01:23:53 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:53 -0200] cupsdReadClient: 14 POST / HTTP/1.1
D [03/Nov/2011:01:23:53 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:53 -0200] cupsdAuthorize: No authentication data provided.
D [03/Nov/2011:01:23:53 -0200] cupsdReadClient: 14 1.1 Get-Jobs 1
D [03/Nov/2011:01:23:53 -0200] Get-Jobs ipp://localhost/printers/
D [03/Nov/2011:01:23:53 -0200] [Job 69] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 69] Unable to open job control file "/var/spool/cups/c00069": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 70] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 70] Unable to open job control file "/var/spool/cups/c00070": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 71] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 71] Unable to open job control file "/var/spool/cups/c00071": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 72] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 72] Unable to open job control file "/var/spool/cups/c00072": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 73] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 73] Unable to open job control file "/var/spool/cups/c00073": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 74] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 74] Unable to open job control file "/var/spool/cups/c00074": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 75] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 75] Unable to open job control file "/var/spool/cups/c00075": No such file or directory
D [03/Nov/2011:01:23:53 -0200] [Job 76] Loading attributes...
E [03/Nov/2011:01:23:53 -0200] [Job 76] Unable to open job control file "/var/spool/cups/c00076": No such file or directory
D [03/Nov/2011:01:23:53 -0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Nov/2011:01:23:53 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdAuthorize: No authentication data provided.
D [03/Nov/2011:01:23:54 -0200] cupsdIsAuthorized: username=""
D [03/Nov/2011:01:23:54 -0200] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [03/Nov/2011:01:23:54 -0200] cupsdCloseClient: 14
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdAcceptClient: 14 from localhost (Domain)
D [03/Nov/2011:01:23:54 -0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdAuthorize: Authorized as user using PeerCred
D [03/Nov/2011:01:23:54 -0200] cupsdIsAuthorized: username="user"
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdAuthorize: Authorized as user using PeerCred
D [03/Nov/2011:01:23:54 -0200] cupsdIsAuthorized: username="user"
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdAuthorize: Authorized as user using PeerCred
D [03/Nov/2011:01:23:54 -0200] cupsdIsAuthorized: username="user"
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdAuthorize: Authorized as user using PeerCred
D [03/Nov/2011:01:23:54 -0200] cupsdIsAuthorized: username="user"
I [03/Nov/2011:01:23:54 -0200] Installing config file "/etc/cups/cupsd.conf"...
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [03/Nov/2011:01:23:54 -0200] cupsdCloseClient: 14
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [03/Nov/2011:01:23:54 -0200] Generating printcap /var/run/cups/printcap...
D [03/Nov/2011:01:23:54 -0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [03/Nov/2011:01:23:54 -0200] Unknown directive JobPrivateAccess on line 88.
E [03/Nov/2011:01:23:54 -0200] Unknown directive JobPrivateValues on line 89.
E [03/Nov/2011:01:23:54 -0200] Unknown directive SubscriptionPrivateAccess on line 90.
E [03/Nov/2011:01:23:54 -0200] Unknown directive SubscriptionPrivateValues on line 91.
W [03/Nov/2011:01:23:54 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/HPCP3505nNTI_Gray__' has already been added
W [03/Nov/2011:01:23:54 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/HPCP3505nNTI_CMYK__' has already been added
W [03/Nov/2011:01:23:54 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/HPCP3505nPRACE_Gray__' has already been added
W [03/Nov/2011:01:23:54 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/HPCP3505nPRACE_CMYK__' has already been added
W [03/Nov/2011:01:23:54 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_S600_Series_Gray__' has already been added
W [03/Nov/2011:01:23:54 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_S600_Series_RGB__' has already been added
W [03/Nov/2011:01:23:55 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/S600_Series_Gray__' has already been added
W [03/Nov/2011:01:23:55 -0200] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/S600_Series_RGB__' has already been added


Really, I can't figure it out by myself. Any help is appreciated!

Thanks in advance...

---

### Post by asterix276 on 2011-11-13
I am having the same problem with a cannon ip2600 printer. Dont know if this is a same issue

Here's the log i see that are what appear to be errors

E [13/Nov/2011:22:00:13 -0600] Unknown directive JobPrivateAccess on line 88.
E [13/Nov/2011:22:00:13 -0600] Unknown directive JobPrivateValues on line 89.
E [13/Nov/2011:22:00:13 -0600] Unknown directive SubscriptionPrivateAccess on line 90.
E [13/Nov/2011:22:00:13 -0600] Unknown directive SubscriptionPrivateValues on line 91.

---


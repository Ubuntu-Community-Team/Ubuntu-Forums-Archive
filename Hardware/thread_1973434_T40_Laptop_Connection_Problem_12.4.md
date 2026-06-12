---
title: "T40 Laptop Connection Problem 12.4"
date: 2012-05-04
forum: Hardware
---

### Post by UnCola on 2012-05-04
Hi I wonder if anyone can help here.  I have read many threads and tried some solutions with mixed results.

Upgraded my T40 earlier this week to 12.4, and at first internet was ok but no wireless.  Then increasingly some sites were slow or unreachable.

Wireless was not switched off in BIOS and was working in windows.  Deleting Network Manager and installing WICD got wireless working, but it won't load most sites.  In fact terminal kept having trouble accessing ubuntu.com to update and install, kept getting that message about something wicked having happened.


So now both ethernet and wireless connect but are virtually useless for almost all sites. Can this be fixed?  Would a fresh install of 12.04 just recreate these problems?

It used to be a few versions back this worked flawlessly, connected automatically on start up... every new Ubuntu version seems to make wireless and now ethernet more and more of a nightmare.

Just noticed, this thread really belongs in network and wireless!

---

### Post by UnCola on 2012-05-06
Please could a Mod here move this thread to Networking and Wireless section?

After spending a lot of time I now have this largely solved.  Deleted and purged Network Manager, went over to WICD, where you can tell it where to get DNS,  but those commands seemed to fail, over and over and over.  Had to edit resolve.conf to get it to access an external source instead of 127.0.0.1.

The unresolved problem is that that resolve.conf gets rewritten on boot or wake from suspend.   And WICD has trouble with WPA passwords and apparently cannot connect to networks that do not broadcast their names - it seems to want to scan for networks and only let you connec to ones it finds.

See these other threads for some T40 info
[http://ubuntuforums.org/showthread.php?t=1861036](http://ubuntuforums.org/showthread.php?t=1861036)
			[http://ubuntuforums.org/showthread.php?t=1838414http://ubuntuforums.org/showthread.php?t=1861036](http://ubuntuforums.org/showthread.php?t=1838414http://ubuntuforums.org/showthread.php?t=1861036)
			[http://ubuntuforums.org/showthread.php?t=1838414](http://ubuntuforums.org/showthread.php?t=1838414)

resolve.conf info
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/989900](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/989900)


Every upgrade seems to bring new, unexplained and very time consuming wireless problems.  Not good enough for the non-geek I'd say - Canonical really should try to improve in this area - if you can't connect you can't use it and you can't recommend it.

On a positive note, the Suspend feature seems to work again, but I no longer have a choice of Hibernate (which always failed anyway).

---


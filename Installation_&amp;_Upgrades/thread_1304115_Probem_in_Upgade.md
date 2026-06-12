---
title: "Probem in Upgade"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by nbsanthosh on 2009-10-28
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I am getting this error on the request for upgrade 

Request for help

---

### Post by johninsf on 2009-10-29
I got a similar error. Please help.

~90% install complete, I got an error related to the KDE Wallet Application. The installation then froze.

After re-boot, I get the same error mentioned here alomg with:

"W: Not using locking for read only lock file /var/lib/dpkg/lock" then 

"dpkg: unable to access dpkg status area: read only file system."

---

### Post by alexcuervo on 2009-10-30
This is how i Fixed this issue.
1)
```
fsck
```
2)
```
mount -n -o remount,rw /
```
3)
```
dpkg --configure -a
```

---

### Post by Sonicgoo on 2009-11-01
So I had a computer that froze during the updgrade of UbuntuStudio and this got me going again. 

I was getting the following error after starting dpkg. 
unable to access dpkg status area: Read-only file system

I have not fixed the problem yet but this got the upgrade going again.

---

### Post by henrychapman on 2009-11-01
When upgrading to KK 9.1 from JJ 9.04 I could not boot and received a cryptic kernel error message. Next I downloaded AND TESTED the KK 9.1 ISO file. I tried a clean install. It booted, but immediately froze and crashed.

I gave up and reinstalled JJ 9.04 which works fine. I have and old IBM Thinkpad X31. I have no other operating systems installed on this PC. Should I forget about KK 9.1?

Thank you.

---


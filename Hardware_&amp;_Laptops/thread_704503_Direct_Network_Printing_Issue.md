---
title: "Direct Network Printing Issue"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by AvgUser on 2008-02-22
Hello All & Thanks for all the hard work!  Ubuntu has come a long way in making a real OS alternative for the masses.  All we need is a bit more polishing, it should not take 2 hrs to regain control of your numlock keys after update mgr runs...

I have an IBM Network Printer 12 [[4312] PCL only, no PS Simm] setup via direct IP.  I have the printer configured using: socket://192.168.1.10:2501   I am able to print a test page with no problems but no real print jobs will flow... The print que states "processing" than changes to "stopped".  The printer works in this configuration via XP systems flawlessly...

The system supports this printer; Do I need to install a PPD file? (Where to get one?)
Does anyone have any experience with these printers via Direct IP Printing under Ubuntu??

```
E [22/Feb/2008:11:07:47 -0600] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [22/Feb/2008:11:08:55 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [22/Feb/2008:11:08:59 -0600] [Job 26] No %%BoundingBox: comment in header!
E [22/Feb/2008:11:09:46 -0600] [Job 27] pdftops-options: -cfg /etc/cups/pdftops.conf
E [22/Feb/2008:11:09:46 -0600] [Job 27] /usr/bin/pdftops exited with  exit code 1
E [22/Feb/2008:11:09:46 -0600] PID 11384 (/usr/lib/cups/filter/pdftops) stopped with status 1!
E [22/Feb/2008:11:09:46 -0600] [Job 27] Empty print file!
E [22/Feb/2008:11:09:46 -0600] PID 11386 (/usr/lib/cups/filter/pstops) stopped with status 1!
E [22/Feb/2008:11:09:52 -0600] [Job 27] Job stopped due to filter errors.
E [22/Feb/2008:11:18:34 -0600] cupsdAuthorize: Local authentication certificate not found!
E [22/Feb/2008:11:18:34 -0600] cupsdAuthorize: Local authentication certificate not found!
E [22/Feb/2008:11:18:42 -0600] cupsdAuthorize: Local authentication certificate not found!
E [22/Feb/2008:11:18:42 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [22/Feb/2008:11:18:44 -0600] [Job 28] No %%BoundingBox: comment in header!
E [22/Feb/2008:11:30:35 -0600] [Job 28] No %%BoundingBox: comment in header!
E [22/Feb/2008:11:33:30 -0600] [Job 30] pdftops-options: -cfg /etc/cups/pdftops.conf
E [22/Feb/2008:11:33:30 -0600] [Job 30] /usr/bin/pdftops exited with  exit code 1
E [22/Feb/2008:11:33:30 -0600] [Job 30] Empty print file!
E [22/Feb/2008:11:33:30 -0600] PID 11536 (/usr/lib/cups/filter/pstops) stopped with status 1!
E [22/Feb/2008:11:33:30 -0600] PID 11534 (/usr/lib/cups/filter/pdftops) stopped with status 1!
E [22/Feb/2008:11:35:06 -0600] [Job 30] Job stopped due to filter errors.
E [22/Feb/2008:11:36:20 -0600] [Job 30] pdftops-options: -cfg /etc/cups/pdftops.conf
E [22/Feb/2008:11:36:20 -0600] [Job 30] /usr/bin/pdftops exited with  exit code 1
E [22/Feb/2008:11:36:20 -0600] [Job 30] Empty print file!
E [22/Feb/2008:11:36:20 -0600] PID 11552 (/usr/lib/cups/filter/pstops) stopped with status 1!
E [22/Feb/2008:11:36:20 -0600] PID 11550 (/usr/lib/cups/filter/pdftops) stopped with status 1!
E [22/Feb/2008:11:36:26 -0600] [Job 30] Job stopped due to filter errors.
```

avguser@sciolism:~$ lpstat -a
PDF accepting requests since Wed 09 Jan 2008 01:42:59 AM CST
Shredder accepting requests since Fri 22 Feb 2008 11:36:26 AM CST

Ubuntu hardy (development branch) \n \l
2.6.24-8-generic

All updates are Current as of this posting...

Thanks in Advance!
:confused:

---

### Post by AvgUser on 2008-02-29
Apparently I am the only person to have this issue...  I suppose it is a good thing the Ubuntu Team pushed out an updated version of CUPS.  Upon completion of this update, printing works fine from Hardy (cups 1.3.6-1ubuntu1)...

Hopefully, moving fwd this will not be broken again arbitrarily...

---


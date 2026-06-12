---
title: "Canon UFRII Shared to Windows - prints test page fine, but Excel/Word/PDF garbled"
date: 2013-02-22
forum: Hardware
---

### Post by MrGregLund on 2013-02-22
Using Ubuntu 12.04 Server (64-bit).
Canon ImageRunner Advance C2030 printer
Using Canon's driver (Installed using steps found in [http://ubuntuforums.org/showthread.php?t=2021854](http://ubuntuforums.org/showthread.php?t=2021854))

Test pages print fine from the server, from Mac clients and from Windows clients.  However, if users try to print excel spreadsheets or word documents (from Mac or Windows), the printer spews out pages and pages, many of them having a line of garbled symbols at the top.

The printer is connected via USB to the Ubuntu box.

This problem is eerily similar to [https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/994477](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/994477), but according to that report, it should be fixed in the version of cups filters that I currently have (1.0.18-0).

The cups error log has the following lines in it, but they don't correspond directly to the timing or number of print jobs that have been garbled:

W [22/Feb/2013:17:02:34 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_iR-ADV_C2020_2030_UFR_II-Gray..' already exists
W [22/Feb/2013:17:02:34 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_iR-ADV_C2020_2030_UFR_II-RGB..' already exists
W [22/Feb/2013:17:02:34 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon_iR-ADV_C2020_2030_UFR_II' already exists
W [22/Feb/2013:17:02:57 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_iR-ADV_C2020_2030_UFR_II-Gray..' already exists
W [22/Feb/2013:17:02:57 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_iR-ADV_C2020_2030_UFR_II-RGB..' already exists
W [22/Feb/2013:17:02:57 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon_iR-ADV_C2020_2030_UFR_II' already exists
W [22/Feb/2013:17:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_iR-ADV_C2020_2030_UFR_II-Gray..' already exists
W [22/Feb/2013:17:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_iR-ADV_C2020_2030_UFR_II-RGB..' already exists
W [22/Feb/2013:17:03:09 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon_iR-ADV_C2020_2030_UFR_II' already exists

---

### Post by MrGregLund on 2013-03-04
I solved this problem by reinstalling everything.  I basically followed the directions of [http://ubuntuforums.org/showthread.php?t=2021854](http://ubuntuforums.org/showthread.php?t=2021854) in reverse, uninstalled CUPS, and rebooted for good measure. I reinstalled CUPS and then repeated the directions again.  I believe I must have missed a step the first time around, or made a typo.

I then made sure all the client computers reinstalled the printer drivers again, and all seems to be working snappy.

---


---
title: "APC UPS system tray missing on xubuntu 12.04 since kernel upgrade"
date: 2014-06-04
forum: Hardware
---

### Post by jimerly on 2014-06-04
I am running Xubuntu 12.04 with apcupsd 3.14.10-1 and recently did a huge kernel upgrade from the repositories (3.2 to 3.13).  The APC UPS tray icon no longer appears.  All other APC communications continue to work flawlessly:  command line tests, stopping/starting service, Apache web page, apcups log notes USB disconnect/reconnect.

Not a huge deal, but annoying.  Anyone have this problem and found a solution?  Thanks.

---

### Post by tgalati4 on 2014-06-04
There are several notification frameworks and they are easy to break when updating the kernel.  Since the basic functions of apcupsd work, including auto-shutdown on power-loss--you should check this, because this is the most important function, you need to dig into how notifications work.  Those notifications get fed into the system tray.  So either the tray is broken or the notifications are broken.

What was the critical function that you needed from the System Tray?  A work-around would be to write a script using *zenity* to get the same information.

Some reading:  [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

You could try uninstalling and reinstalling and that might trigger an extra library to be installed that would fix your problem.  Otherwise, you will have to dig into the details and/or file a bug against *apcupsd* and kernel 3.13.

Why did you upgrade the kernel?  Was the 3.2 kernel not working on your hardware?

---

### Post by jimerly on 2014-06-04
The latest version of 3.2 (3.2.0-64) caused my external USB 3.0 backup drive to stop working.  If the drive was connected during boot, a repeating modprobe message prevented a full boot.  I will try your suggestion for uninstalling and reinstalling.

---

### Post by tgalati4 on 2014-06-05
That is certainly a valid reason for upgrading the kernel.  As you know you have older sub-versions of your 3.2 kernel that you could boot into as a work-around.  I would file a bug against the 3.2.0-64 kernel as a regression.  I hate when something that was working fine breaks with an update--something that happens all to often in linux.  Moving from kernel 3.2 to 3.13 is a large jump, so I would expect many regressions--especially with older hardware.

---


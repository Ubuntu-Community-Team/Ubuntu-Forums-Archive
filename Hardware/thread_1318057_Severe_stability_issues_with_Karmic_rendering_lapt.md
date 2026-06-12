---
title: "Severe stability issues with Karmic rendering laptop unusable"
date: 2009-11-07
forum: Hardware
---

### Post by bernie9998 on 2009-11-07
Ever since upgrading my Lenovo IdeaPad Y530 from Jaunty to Karmic, I have been plagued with severe stability issues, rendering my laptop essentially useless.

With 9.10, my laptop has been plagued with sudden reboots, kernel panics, and complete system lock ups, none of which had been experienced before with Jaunty.  Even worse, I've received an odd error message suggesting that the system is silently corrupting data that is accessed from my HD.

While trying to extract a file from a bzipped tar archive, I received an error message of an unexpected end of file.  When I rebooted into an old Jaunty live cd, I was able to extract the file without issue.

These issues are being experienced on a clean install of Karmic.  In fact, the install had to be attempted twice as the laptop had suddenly rebooted during the first attempt.

I would like to try to troubleshoot this issue, but I had no idea where to start-- I think these issues might be related to disk activity, but have no way of confirming this.

Has anyone else been experiencing similar issues?

---

### Post by teddersion on 2009-11-30
Hi,

I have had very similar issues with a 9.10 Karmic install, only mine is on an HP Compaq desktop. My main problem has been that the system will freeze up and become unresponsive to anything other than mouse cursor movement. The only way I've found to unlock the system is to do a hard restart. Fortunately, I have not seen any data corruption occurrences, but thanks for the alert to that possibility.

I have not been able to find any reliable way to replicate the problem, but I can estimate that it is not a desktop environment-related problem, as I have had it happen in Gnome, KDE, and Xfce. 

If anyone has any suggestions as to how these problems might be prevented, it would be greatly appreciated.

Thank you very much.

---

### Post by bernie9998 on 2009-11-30
There is a newer thread regarding this issue here:
[http://ubuntuforums.org/showthread.php?t=1318019](http://ubuntuforums.org/showthread.php?t=1318019)

I have since managed to work around this issue by installing a newer kernel which appears to have these issues resolved.  The above thread has more details.

---


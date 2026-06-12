---
title: "Canon Pro 9500, printing problems"
date: 2014-02-16
forum: Hardware
---

### Post by tashimee2 on 2014-02-16
Since the last time Ubuntu 12.04 updated I haven't been able to print anything. I get the error message: unknown:1320. Would someone please tell me what this means and how to correct it.

---

### Post by aikishugyo on 2014-02-16
Only reference to such an error I could Google:
[http://www.turboprint.de/support/viewtopic.php?t=707](http://www.turboprint.de/support/viewtopic.php?t=707)
And no hint on where it is reported.
Anhow, solution there was to reinstall the driver (in his case it was Turboprint) and restart the OS.
Perhaps you can try. Else, more info on printer, driver version, and CUPS logs needed.

---

### Post by tashimee2 on 2014-02-17
I tried uninstalling and reinstalling, rebooting, and I'm still getting the same error. I tried to load a later version of Turboprint, same error. My printer is a Canon Pro 9500 mark II, Turboprint 2.21-1. How do I get the CUPS logs?

---

### Post by aikishugyo on 2014-02-17
CUPS access and error logs you can access from the admin panel of the CUPS web interface. Have to set debug on to get anything useful first.
The file itself is in /var/log/cups/error.log

---

### Post by tashimee2 on 2014-02-19
tashimee@tashimee-desktop:~$ tail -f /var/log/cups/error_log
E [19/Feb/2014:07:23:58 -0500] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [19/Feb/2014:07:23:58 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Pro9500II-TurboPrint-Gray..' already exists
W [19/Feb/2014:07:23:58 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Pro9500II-TurboPrint-RGB..' already exists
W [19/Feb/2014:07:23:58 -0500] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Pro9500II-TurboPrint' already exists
E [19/Feb/2014:07:58:54 -0500] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [19/Feb/2014:08:11:00 -0500] [Job 2] Printer error!

---


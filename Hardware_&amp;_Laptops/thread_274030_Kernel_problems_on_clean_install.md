---
title: "Kernel problems on clean install"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by arran on 2006-10-09
Hi,

I've got problems after installing Ubuntu 6.06 LTS on my Laptop.
Laptop is 1.6 Centrino, 1GB ram, 100GB HD and mostly works OK.

Ubuntu runs beautifully if run from the Live CD or if booted in recovery mode as described below.

Can anyone point me in the right direction for finding out what is failing. I'm new to Linux but experienced with Win XP.

If booted normally the boot process is slow both before and after login.  I get a hw_random error from a clean install but I can sort that.  About 70% of the time I get an 'Internal error - failed to initialise HAL' and then usb devices do not work.  I've tried a number of fixes from these forums but the one below is the closest I've got to a working system. I cannot find any error in the syslog.

If I boot in recovery mode, and run # /etc/init.d/dbus start
both DBUS and HAL start sucessfully, I can start the GDM without HAL error, i just haven't got much else running (ACPI for example), but what I have runs beautifully. 

Any advice as to where the failures might be logged, how to expand what is being reported or where to comment out drivers to test would be gratefully received.

Thanks in Advance

---


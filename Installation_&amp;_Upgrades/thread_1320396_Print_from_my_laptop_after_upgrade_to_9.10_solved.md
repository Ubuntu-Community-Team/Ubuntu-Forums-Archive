---
title: "Print from my laptop after upgrade to 9.10 solved"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by kdavies on 2009-11-09
After upgrading to 9.10

I wanted to be able to print from the printer attached to the desktop.

Installed cupsys and client
as root
 apt-get install cupsys cupsys-client

created the /etc/cups/client.conf file and entered my desktop pc details.
restarted the cups system
/etc/init.d/cups restart

From the menu
 System-> administration -> printing

The printer is there.

These two articles explain printing on Unix, linux, Ubuntu
[Set up CUPS]("http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html")  with more help at [Help Ubuntu]("https://help.ubuntu.com/9.10/printing/C/printing.html")

---


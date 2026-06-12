---
title: "Daily 12.04 Update broke CUPS: 631 - Cannot assign requested address"
date: 2012-06-01
forum: Hardware
---

### Post by roots on 2012-06-01
Hi there,

Ubuntu 12.04 daily update yesterday broke CUPS functionality for me. I'm getting error messages in /var/log/cups/error_log:

E [31/May/2012:15:31:23 +0200] Unable to bind socket for address [v1.::1]:631 - Cannot assign requested address.

Running U12.04 with a Canon Pixma IP2700 printer.

After purging all CUPS and Canon printer drivers, and just reinstalling CUPS & configuring for Canon IP2700 via http-Interface, I was able to print a test page and 2 office sheets, then the error recurred with no way to print.
When trying to reinstall Canon printer drivers ( cnijfilter-ip2700series-3.30-1-i386-deb) I'm getting the error that no printer is connected, plus /var/log/cups/error_log gets another of the above errors. The printer, however, is connected as lsusb tells. Also, I can print from within a virtualboxed Windows just fine.

Any suggestions?!

---


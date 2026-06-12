---
title: "Printer"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by tqft on 2007-09-26
Am running feisty
Printer: Canon BJC-255 SP installed on parallel port
Went to [http://localhost:631/](http://localhost:631/) CUPS detected printer on Canon port, I had the ppd file handy (you will see why in a minute), flicked some switches (eg A4 rather than US Letter) and all appears installed fine.

print test page - no luck printer times out and switches off before print happens.

This should work.
Printer worked fine with similar setup under Dapper (hence the ppd file handy) - 
[http://forums.mozillazine.org/viewtopic.php?p=2914699&sid=52917030760f8ee822aab70620c86de1](http://forums.mozillazine.org/viewtopic.php?p=2914699&sid=52917030760f8ee822aab70620c86de1)
Was helping a person and it worked for me as well

[https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html](https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html)
I can't do this step as one of the groups Shadow isn't there
"Select the group shadow "

Anyone got any idea?

---

### Post by tqft on 2007-09-26
CUPS error messages from

[http://localhost:631/admin/log/error_log](http://localhost:631/admin/log/error_log)

E [26/Sep/2007:17:10:04 +1000] Creating missing directory "/var/run/cups/certs"
E [26/Sep/2007:18:04:57 +1000] [CGI] Unable to scan "@LOCAL"!
E [26/Sep/2007:18:05:31 +1000] CUPS-Add-Modify-Printer: Unauthorized
E [26/Sep/2007:18:05:35 +1000] CUPS-Add-Modify-Printer: Unauthorized
E [26/Sep/2007:18:05:56 +1000] CUPS-Add-Modify-Printer: Unauthorized
E [26/Sep/2007:18:08:47 +1000] [CGI] Unable to scan "@LOCAL"!
E [26/Sep/2007:18:11:27 +1000] [CGI] Unable to scan "@LOCAL"!
E [27/Sep/2007:06:56:05 +1000] [CGI] Unable to scan "@LOCAL"!
E [27/Sep/2007:06:56:07 +1000] [CGI] Unable to scan "@LOCAL"!

---


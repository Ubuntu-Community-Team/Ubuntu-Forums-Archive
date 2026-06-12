---
title: "Printing Problem On Local System"
date: 2008-08-22
forum: General Help
---

### Post by schnarff on 2008-08-22
I've got an HP LaserJet 1150 printer, which I've verified in numerous places is compatible with Ubuntu (in fact, it once printed well, before a previous upgrade). It's connected via USB, and shows up nicely via lsusb:

```
alex@home: /var/log/cups$ lsusb
Bus 003 Device 002: ID 058f:6335 Alcor Micro Corp.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 004: ID 03f0:0f17 Hewlett-Packard
Bus 002 Device 003: ID 0d8c:0008 C-Media Electronics, Inc.
Bus 002 Device 001: ID 0000:0000
```

For some reason, if I go to System -> Administration -> Printing and try "New Printer", not only does it not show up as a local printer, the "Printer Port" list is empty, so I can't go manually specify it that way.

I've been able to get it sort of installed by going to the CUPS web interface at [http://localhost:631/](http://localhost:631/). I say "sort of" because I can successfully print a test page there, but I can't print from anywhere else on the system (Firefox, OpenOffice, etc.).

Looking at /var/log/cups/error_log, I'm seeing messages like these every few seconds:

```
E [22/Aug/2008:17:27:20 -0400] CUPS-Get-Printers: Forbidden
```

they correspond to lines from /var/log/cups/access_log:

```
192.168.2.80 - - [22/Aug/2008:17:27:44 -0400] "POST / HTTP/1.1" 403 75 CUPS-Get-Printers successful-ok
```

This would seem to indicate a permissions issue. The really wacky part, though, is that I've set /etc/cups/cupsd.conf to be about as permissive as physically possible:
```

# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Order allow,deny
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    Order allow,deny
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Order allow,deny
  </Limit>
  <Limit All>
    Order allow,deny
  </Limit>
</Policy>
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf
# Allow remote access
Port 631
```

I'm at a real loss here. Why can't I print?

---

### Post by bmac on 2008-08-22
If you haven't done so, try installing the HPLIP driver. Your printer is supported by this driver.

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Hope this helps....

---


---
title: "setup HP printer Deskjet 5740"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by satimis on 2006-11-26
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64


On adding HP printer, encountered problem on;

Starting with "//localhose:63/admin --> Enter username and password for "CUPS" at [http://localhost:631](http://localhost:631)

Tried root/"root password" and /satimis/"satimis password".  Both did not work.

Please help.  TIA


Edit :-   * * * 

Sorry I forgot mentioning this is a network printer.


Starting with "//localhose:63/admin --> Device for HP_Printer (Device:AppSocket/HP JetDirect) --> Device URI for HP_Printer (socket://hostname) -->  Enter username and password for "CUPS" at [http://localhost:631](http://localhost:631)

$ cat /etc/cups/cupsd.conf```


LogLevel warning

# Administrator user group...
SystemGroup lpadmin

BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#
ServerAdmin satimis@localhost

```

$ cat /etc/cups/cups.d/ports.conf```


Listen 127.0.0.1:631  # existing loopback Listen
#Listen localhost:631
Listen /var/run/cups/cups.sock  # existing socket Listen
Listen 192.168.10.250:631  # Listen on the LAN interface, Port 631 (IPP)
```

I need to have the printer setup locally, not remotely

Tks


B.R.
satimis

---


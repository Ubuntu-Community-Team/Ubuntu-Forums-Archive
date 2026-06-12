---
title: "CUPS: printers not available locally, however remote jobs work"
date: 2008-09-11
forum: General Help
---

### Post by Meson on 2008-09-11
Everything was working fine as this afternoon...  NOW if I try to print from Gedit, Firefox, etc none of my printers show up.  However my printers are shared and remote computers can still use them just fine.

This was the original setup in my cupsd.conf
```

SSLPort 631
Listen /var/run/cups/cups.sock

<Location />
  Order deny,allow
  Deny none
  Allow all

  AuthType Basic
  Encryption Required

  Satisfy all
</Location>

```

With these settings if I log on to [https://localhost:631/printers/PDF](https://localhost:631/printers/PDF) I am able to print a test page.

To view the printers from the printer dialog I had to change the "AuthType" to "None" however the still weren't usable (the Print button was grayed out and the tabs specific to each printer in the print dialog never appeared.)  To get the usable, I had to change "SSLPort 631" to "Listen *:631"  So it looked like this:
```

Listen *:631
Listen /var/run/cups/cups.sock

<Location />
  Order deny,allow
  Deny none
  Allow all

  AuthType None
  Encryption Required

  Satisfy all
</Location>

```

This is all quite odd if you ask me.  Here is my computer cupsd.conf as of this afternoon when printing worked fine.
```

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
SSLPort 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder deny,allow
BrowseDeny none
BrowseAllow all
BrowseAddress @LOCAL
BrowseRemoteOptions encryption=required

# Default authentication type, when authentication is required...
DefaultAuthType Basic
DefaultEncryption Required

# Restrict access to the server...
<Location />
  Order deny,allow
  Deny none
  Allow all

  AuthType Basic
  Encryption Required

  Satisfy all
</Location>


# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
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

```

The only thing that has changed since printing working locally and now is that I took my laptop to school with me and connected to my schools wireless network...  I noticed in class that no printers appeared in the print dialog, however I figured it was just because they were not available (but now that I think about it, the PDF printer should have been there - the cups-pdf:/ printer should not be confused with "Print to File" which has been around all along.)

---


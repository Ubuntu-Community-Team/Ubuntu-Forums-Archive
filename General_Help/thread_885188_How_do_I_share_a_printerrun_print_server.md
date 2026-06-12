---
title: "How do I share a printer/run print server?"
date: 2008-08-09
forum: General Help
---

### Post by Bllz on 2008-08-09
Hello!

I recently installed Mythbuntu and i was hoping to have the box be a print server for wireless clients in the home network.

I noticed that mythbuntu does not have CUPS or any printer-related packages installed, so I did  my best to install CUPS (don't know how well I did it--I did manage to print a web page without hitches).

My question is, from here, what do I need to install to run a print server and how do I configure it to work with both windows and MacOsX clients?

Thanks!
Bllz

---

### Post by ModelM on 2008-08-09
If CUPS is there & working you can access it by pointing your web browser to:

127.0.0.1:631

Just tell CUPS to broadcast your printer & the Apple machine should be able to use it right away. It works very well, probably because Apple owns CUPS.

As to the Windows machine - I wouldn't have the slightest idea.

---

### Post by Bllz on 2008-08-10
ModelM:

Thanks very much for your help.  I accessed the CUPS web interface and enabled the option to "Share published printers connected to this system" under the "administration" tab.

I'm still not seeing the printer in my vista client, so I was wondering if there was a way to confirm that mythbuntu was, in fact, sharing the printer.

Thanks again
Bllz

---

### Post by ModelM on 2008-08-10
Published printers are shared but don't forget to publish the printer. Go to the "printers" tab, select the printer & select "publish this printer".

---

### Post by Meson on 2008-09-08
To add the printer in windows you need to add it using a url like this:

```
http://printserver:631/printers/Printer_Name
```

The http can be https if you've enabled encryption.

the printserver is the DNS name of your printserver, an ip address will do.

631 is the default port of IPP (internet printing protocol - the protocol cups uses to share printers)

and Printer_Name is the name of the printer...


In my experience I've had a lot more success editing the /etc/cups/cupsd.conf configuration file manually than using the web interface.


Here's a sample of my config file:

```

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
SSLListen *:631
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

# Publication on printer creation
DefaultShared no

# Restrict access to the server...
<Location />
  Order deny,allow
  Deny none
  Allow all

  AuthType Basic
  Encryption Required

  Satisfy all
</Location>

# Restrict access to the admin pages...
#<Location /admin>
#  Order allow,deny
#</Location>

# Restrict access to configuration files...
#<Location /admin/conf>
#  AuthType Default
#  Require user @SYSTEM
#  Order allow,deny
#</Location>

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

All of that policy stuff is just the default that was there before I editted the file.  I'm not sure if it even works because of my restrictions in <Location />.

With this setup encryption is required and the username/password of someone in the lpadmin group is required to do everything.  You may want to let users print anonymously by modifying settings in <Location /printers>.

Here is some nice documentation on this file: [http://www.cups.org/documentation.php/ref-cupsd-conf.html](http://www.cups.org/documentation.php/ref-cupsd-conf.html)

---


---
title: "CUPS Error:  foomatic-rip failed"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by Don9307 on 2007-11-18
I'm running ubuntu 7.10 and when attempting to print via my MSHOME network to a Windows Samba Share printer (Lexmark X125) with share name=Lexmark connected to a Windows XP PC at IP=192.168.1.100, when using the URL: **smb://MSHOME/192.168.1.100/Lexmark** in the CUPS printer configuration, the print job is stopped abuptly.  I'm using the recommended Lexmark-X125-drv_x125.ppd driver.  The CUPS configuration ([http://localhost:631](http://localhost:631)) shows Lexmark X125 as **(Default Printer) "/usr/lib/cups/filter/foomatic-rip failed"   **

**The CUPS error-log shows:**
E [18/Nov/2007:19:01:26 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [18/Nov/2007:19:01:36 +0000] [Job 1] No %%BoundingBox: comment in header!
E [18/Nov/2007:19:01:36 +0000] [Job 1] No ticket cache found for userid=0
E [18/Nov/2007:19:01:36 +0000] [Job 1] Can not get the ticket cache for root
E [18/Nov/2007:19:01:36 +0000] PID 6390 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [18/Nov/2007:19:01:36 +0000] [Job 1] Job stopped due to filter errors.
E [18/Nov/2007:19:03:46 +0000] Purge-Jobs: Unauthorized
E [18/Nov/2007:19:03:50 +0000] Purge-Jobs: Unauthorized

**The CUPS access log shows:**
localhost - - [18/Nov/2007:19:11:46 +0000] "GET /printers/ HTTP/1.1" 200 0 - -
localhost - - [18/Nov/2007:19:11:46 +0000] "GET /printers/ HTTP/1.1" 200 8882 - -
localhost - - [18/Nov/2007:19:15:16 +0000] "GET /printers/Lexmark?op=print-test-page HTTP/1.1" 200 0 - -
localhost - - [18/Nov/2007:19:15:16 +0000] "POST /printers/Lexmark HTTP/1.1" 200 17797 Print-Job successful-ok
localhost - - [18/Nov/2007:19:15:16 +0000] "GET /printers/Lexmark?op=print-test-page HTTP/1.1" 200 3417 - -
localhost - - [18/Nov/2007:19:15:17 +0000] "POST / HTTP/1.1" 200 180 Get-Jobs successful-ok
localhost - - [18/Nov/2007:19:15:17 +0000] "POST / HTTP/1.1" 200 180 Get-Jobs successful-ok
localhost - - [18/Nov/2007:19:15:17 +0000] "POST / HTTP/1.1" 200 180 Get-Jobs successful-ok
localhost - - [18/Nov/2007:19:15:17 +0000] "POST / HTTP/1.1" 200 180 Get-Jobs successful-ok
localhost - - [18/Nov/2007:19:15:18 +0000] "GET /printers/Lexmark HTTP/1.1" 200 0 - -
localhost - - [18/Nov/2007:19:15:18 +0000] "POST / HTTP/1.1" 200 458 Get-Jobs successful-ok
localhost - - [18/Nov/2007:19:15:18 +0000] "GET /printers/Lexmark HTTP/1.1" 200 7991 - -
localhost - - [18/Nov/2007:19:15:18 +0000] "GET /images/button-restart-job.gif HTTP/1.1" 200 408 - -
localhost - - [18/Nov/2007:19:15:18 +0000] "GET /images/button-cancel-job.gif HTTP/1.1" 200 377 - -
localhost - - [18/Nov/2007:19:15:18 +0000] "GET /images/button-move-job.gif HTTP/1.1" 200 370 - -
localhost - - [18/Nov/2007:19:15:39 +0000] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [18/Nov/2007:19:15:39 +0000] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found
localhost - - [18/Nov/2007:19:15:39 +0000] "GET /admin HTTP/1.1" 200 6018 - -
localhost - - [18/Nov/2007:19:16:06 +0000] "POST /admin HTTP/1.1" 200 62 - -
localhost - - [18/Nov/2007:19:16:06 +0000] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - - [18/Nov/2007:19:16:06 +0000] "POST /admin HTTP/1.1" 401 62 - -
localhost - - [18/Nov/2007:19:16:06 +0000] "POST /admin HTTP/1.1" 200 62 - -
localhost - donald [18/Nov/2007:19:16:06 +0000] "POST /admin HTTP/1.1" 200 62 - -
localhost - - [18/Nov/2007:19:16:06 +0000] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - donald [18/Nov/2007:19:16:06 +0000] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 1654 - -
localhost - donald [18/Nov/2007:19:16:06 +0000] "POST /admin HTTP/1.1" 200 3456 - -
localhost - donald [18/Nov/2007:19:16:11 +0000] "GET /admin/?OP=redirect HTTP/1.1" 200 0 - -
localhost - donald [18/Nov/2007:19:16:11 +0000] "GET /admin/?OP=redirect HTTP/1.1" 200 0 - -
localhost - donald [18/Nov/2007:19:16:11 +0000] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [18/Nov/2007:19:16:11 +0000] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found

**My CUPS Configuration FIle reads:**
LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow localhost
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

**The Windows printer share is accessible, per the CUPS configuration GUI.  Does anyone have any suggestions as to how I can get this working?**:confused:

---

### Post by Don9307 on 2007-11-19
In case anyone is wondering, I've tried **sudo aa-complain cupsd** and it didn't work for me.

---

### Post by j8a on 2008-04-07
/usr/lib/cups/filter/foomatic-rip failed

The problem began when I accepted the cups update a week ago. Anyone know who I can fix this problem?

---


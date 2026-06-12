---
title: "Printer not working"
date: 2017-03-13
forum: Hardware
---

### Post by stefworld on 2017-03-13
I'm using ubuntu 14.04.5 with cups 1.7.2.

After installing a printer and trying to print a test page i get the follow error:

```
**Inactief - File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).**

**Cups error log:**

[I]E [13/Mar/2017:09:12:06 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:06 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:06 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:15 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:15 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:15 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:31 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:31 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:31 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:33 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:12:33 +0100] [Job 21] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:12:33 +0100] [Job 21] Stopping job because the scheduler could not execute a filter.
E [13/Mar/2017:09:14:28 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:14:28 +0100] [Job 22] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:14:28 +0100] [Job 22] Stopping job because the scheduler could not execute a filter.
W [13/Mar/2017:09:15:30 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Printer58-Gray..' already exists
E [13/Mar/2017:09:15:30 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:15:30 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:15:30 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:15:30 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:15:30 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:15:44 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:15:44 +0100] [Job 23] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:15:44 +0100] [Job 23] Stopping job because the scheduler could not execute a filter.
E [13/Mar/2017:09:16:09 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:16:09 +0100] [Job 24] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:16:09 +0100] [Job 24] Stopping job because the scheduler could not execute a filter.
E [13/Mar/2017:09:16:23 +0100] [Client 22] pam_authenticate() returned 7 (Authentication failure)
E [13/Mar/2017:09:16:45 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:16:45 +0100] [Job 25] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:16:45 +0100] [Job 25] Stopping job because the scheduler could not execute a filter.
E [13/Mar/2017:09:23:35 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:23:35 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:23:35 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:23:35 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:23:41 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:23:41 +0100] [Job 26] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:23:41 +0100] [Job 26] Stopping job because the scheduler could not execute a filter.
E [13/Mar/2017:09:28:42 +0100] [Job 26] Stopping unresponsive job.
E [13/Mar/2017:09:36:37 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:36:37 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:36:37 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:36:37 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:36:51 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:36:51 +0100] [Job 27] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:36:51 +0100] [Job 27] Stopping job because the scheduler could not execute a filter.
W [13/Mar/2017:09:37:22 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Printer58-Gray..' already exists
E [13/Mar/2017:09:37:22 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:37:22 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:37:22 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:37:24 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:37:24 +0100] [Job 28] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:37:24 +0100] [Job 28] Stopping job because the scheduler could not execute a filter.
E [13/Mar/2017:09:42:15 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:15 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:15 +0100] Brother-DCP-1200: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:29 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:29 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:29 +0100] Printer58: File "/usr/lib/cups/filter/rastertort58_80" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:30 +0100] Printer58: File "/usr/lib/cups/filter/bannertopdf" has insecure permissions (0100777/uid=0/gid=0).
E [13/Mar/2017:09:42:30 +0100] [Job 29] Unable to start filter "bannertopdf" - Success.
E [13/Mar/2017:09:42:30 +0100] [Job 29] Stopping job because the scheduler could not execute a filter.[/I]
```


**Cups config file:**

```
[I]#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#[/I]
```

what can be the reason for this?

---

### Post by ajgreeny on 2017-03-13
Please use **Code-Tags** in future for terminal output or any text from config files or logs. See my signature below for a **How-to**
It formats output properly and makes it a lot easier to read.

---

### Post by slickymaster on 2017-03-13
*Thread moved to **Hardware**.*

---

### Post by oldrocker99 on 2017-03-13
Are you using the Brother Linux drivers? I have a Brother HL-3170CDW, and it's likely the easiest printer driver process I've ever used. You need to enter the model number, and the IP address of the printer (mine is 10.10.10.160) and you're set.

---

### Post by pdc on 2017-03-13
Hi stefworld; welcome to the Ubuntu forums; can I try to find out a little more about how you are connected;

1) "I'm using ubuntu 14.04.5 with cups 1.7.2."     .......... you are using someone else's system? ....... it's an install that has been in for a while

2) it's a network connection ... can you tell us a little more ...

3) The Brother DCP-1200 is I see a discontinued model; it seems to be a large, stand-alone MFD with colour laser  [http://www.brother-usa.com/Printer/ModelDetail/1/DCP1200/Overview](http://www.brother-usa.com/Printer/ModelDetail/1/DCP1200/Overview) ..... so when I go to Open Printing, it is not mentioned at all for support there, and no mention on Brother's site

___________

if I paste in one of your error messages .........
```
/usr/lib/cups/filter/foomatic-rip" has insecure permissions (0100[SIZE=4]**777**[/SIZE])
```

I guess one could see why the system is distressed: to me, 777 means anyone can read, write, execute ....... as per thumbnail (which comes from here [http://www.linux.org/threads/file-permissions-chmod.4094/](http://www.linux.org/threads/file-permissions-chmod.4094/))

when I do ```
ls -l /usr/lib/cups/filter/foomatic-rip
``` on our system, I get ```
-rwxr-xr-x 1 root root 110600 Aug 22  2016
``` ......which in numbers I think is 751  .........read,write,execute (4+2+1)    ........ read,execute (4+1) ......... execute (1)

........ so it saying when you issue the command there are three rankings:  OWNER : GROUP : WORLD :        so **owner** (root) can [COLOR="#008000"]read, write, execute[/COLOR]     **group** (root) can [COLOR="#008000"]read, execute[/COLOR]   **world** can [COLOR="#008000"]execute[/COLOR] 

........ when you have a 777, the final group or WORLD (or anyone!!) ....... can read, write, execute ......... so no protected castle for your system files ............. 

_________

one could recommend some "chmod" phrases I guess; but maybe we just check out how things are where they are first of all; ............. naturally, some folks find a clean install of a new system means new settings that are secure

---


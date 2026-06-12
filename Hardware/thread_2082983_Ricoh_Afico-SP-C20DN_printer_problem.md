---
title: "Ricoh Afico-SP-C20DN printer problem"
date: 2012-11-11
forum: Hardware
---

### Post by toto16430 on 2012-11-11
Hi,


My ubuntu version is update to 12.04 and now I have problems printer.
When I install driver printer, I don't have problem and I can print test page.



But I can't print all files. I can see on my screen :
Error printer
printer "Afico-SP-C20DN":
" connecting to device".


Sorry for my bad english.

Can you help me ?




info@info:~$ tail -n 100 -f /var/log/cups/error_log
W  [09/Nov/2012:08:20:13 +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-Gray..' already exists
W [09/Nov/2012:08:20:13  +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-CMYK..' already exists
W [09/Nov/2012:08:20:13  +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Aficio-SP-C420DN' already exists
W [09/Nov/2012:08:20:13 +0100]  failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-Gray..' already exists
W [09/Nov/2012:08:20:13  +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-CMYK..' already exists
W [09/Nov/2012:08:20:13  +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Aficio-SP-C420DN' already exists
W [09/Nov/2012:10:24:02 +0100]  failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-Gray..' already exists
W [09/Nov/2012:10:24:02  +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-CMYK..' already exists
W [09/Nov/2012:10:24:02  +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Aficio-SP-C420DN' already exists
W [09/Nov/2012:10:32:24 +0100]  failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-Gray..' already exists
W [09/Nov/2012:10:32:24  +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-CMYK..' already exists
W [09/Nov/2012:10:32:24  +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Aficio-SP-C420DN' already exists
W [09/Nov/2012:10:32:24 +0100]  failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-Gray..' already exists
W [09/Nov/2012:10:32:24  +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists: profile id  'Aficio-SP-C420DN-CMYK..' already exists
W [09/Nov/2012:10:32:24  +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Aficio-SP-C420DN' already exists




cupsd.conf
#
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

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
< Location / >
  Order allow,deny
< /Location >

# Restrict access to the admin pages...
< Location /admin >
  Order allow,deny
< /Location >

# Restrict access to configuration files...
< Location /admin/conf >
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
< /Location >

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  < Limit Create-Job Print-Job Print-URI Validate-Job >
    Order deny,allow
  < /Limit >

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  < /Limit >

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  < /Limit >

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  < /Limit >

  # Only the owner or an administrator can cancel or authenticate a job...
  < Limit Cancel-Job CUPS-Authenticate-Job >
    Require user @OWNER @SYSTEM
    Order deny,allow
  < /Limit >

  < Limit All >
    Order deny,allow
  < /Limit >
< /Policy >

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  < Limit Create-Job Print-Job Print-URI Validate-Job >
    AuthType Default
    Order deny,allow
  < /Limit >

  < Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document >
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  < /Limit >

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
#








printers.conf
# Printer configuration file for CUPS v1.5.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
< DefaultPrinter RICOH-Aficio-SP-C420DN >
UUID urn:uuid:69342c28-00fe-37d2-70c3-8bf22a31d23e
Info RICOH Aficio SP C420DN
Location 
MakeModel Ricoh Aficio SP C420DN PS
DeviceURI dnssd://RICOH%20Aficio%20SP%20C420DN._pdl-datastream._tcp.local/
State Idle
StateTime 1352620841
Type 8425692
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Attribute marker-colors \#000000,none,none,none,none
Attribute marker-levels -1,-1,-1,-1,-1
Attribute marker-names Toner noir,þÿÿÿýÿÿÿToner usagÃ©,,,
Attribute marker-types toner,unknown,unknown,unknown,unknown
Attribute marker-change-time 1352620902
</Printer>

---


---
title: "HP Deskjet 9800 very slow printing"
date: 2015-10-13
forum: Hardware
---

### Post by cscj01 on 2015-10-13
I run ubuntu 14.04.3 x64 and have an HP Deskjet 9800.  Until recently, the printer functioned flawlessly.  Finally, the printer would not raise the paper, so I could not print from the main tray.  I had to rotate the wheel inside the printer to get the paper lifter properly positioned.  After that the printer started feeding from the main tray again.  However, printing became very slow.  Sometimes there are long pauses between the printing of individual lines in a document.  It can take hours to print a 50 page document.  The printer never did this before.  Does anyone have any suggestions of how I might go about trying to fix this problem?

---

### Post by agillator on 2015-10-13
How old is the printer? Have you recently upgraded your system? Are you connected to it by usb, ethernet or wireless? Are you using HPLIP or some other driver? What is your quality of print set to: normal, best, draft? Have you changed or upgraded the program you are printing from? Any of these could have an impact.

---

### Post by tgalati4 on 2015-10-13
Look in /var/log/cups for errors.  If you don't find any, then start looking at the printer itself.  Unplug it for 10 minutes and then turn it back on, then quickly print.  If it works ok, then you know you have an intermittent problem.

---

### Post by cscj01 on 2015-10-16
> **tgalati4 said:**
> Look in /var/log/cups for errors.  If you don't find any, then start looking at the printer itself.  Unplug it for 10 minutes and then turn it back on, then quickly print.  If it works ok, then you know you have an intermittent problem.

I have this from a log file for which I was printing a 57 page document file:```
E [12/Oct/2015:08:02:39 -0400] Unknown directive BrowseAddress on line 8 of /etc/cups/cupsd.conf.
W [12/Oct/2015:08:02:39 -0400] No limit for Validate-Job defined in policy default and no suitable template found.
W [12/Oct/2015:08:02:39 -0400] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [12/Oct/2015:08:02:39 -0400] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [12/Oct/2015:08:02:39 -0400] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [12/Oct/2015:08:02:39 -0400] No JobPrivateAccess defined in policy default - using defaults.
W [12/Oct/2015:08:02:39 -0400] No JobPrivateValues defined in policy default - using defaults.
W [12/Oct/2015:08:02:39 -0400] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [12/Oct/2015:08:02:39 -0400] No SubscriptionPrivateValues defined in policy default - using defaults.
W [12/Oct/2015:08:02:39 -0400] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.
W [12/Oct/2015:08:02:39 -0400] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [12/Oct/2015:08:02:39 -0400] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [12/Oct/2015:08:02:39 -0400] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [12/Oct/2015:08:02:39 -0400] No JobPrivateAccess defined in policy authenticated - using defaults.
W [12/Oct/2015:08:02:39 -0400] No JobPrivateValues defined in policy authenticated - using defaults.
W [12/Oct/2015:08:02:39 -0400] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [12/Oct/2015:08:02:39 -0400] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
E [12/Oct/2015:11:53:50 -0400] Unknown directive BrowseAddress on line 8 of /etc/cups/cupsd.conf.
W [12/Oct/2015:11:53:50 -0400] No limit for Validate-Job defined in policy default and no suitable template found.
W [12/Oct/2015:11:53:50 -0400] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [12/Oct/2015:11:53:50 -0400] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [12/Oct/2015:11:53:50 -0400] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [12/Oct/2015:11:53:50 -0400] No JobPrivateAccess defined in policy default - using defaults.
W [12/Oct/2015:11:53:50 -0400] No JobPrivateValues defined in policy default - using defaults.
W [12/Oct/2015:11:53:50 -0400] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [12/Oct/2015:11:53:50 -0400] No SubscriptionPrivateValues defined in policy default - using defaults.
W [12/Oct/2015:11:53:50 -0400] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.
W [12/Oct/2015:11:53:50 -0400] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [12/Oct/2015:11:53:50 -0400] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [12/Oct/2015:11:53:50 -0400] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [12/Oct/2015:11:53:50 -0400] No JobPrivateAccess defined in policy authenticated - using defaults.
W [12/Oct/2015:11:53:50 -0400] No JobPrivateValues defined in policy authenticated - using defaults.
W [12/Oct/2015:11:53:50 -0400] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [12/Oct/2015:11:53:50 -0400] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
```The 2 errors are the same.  /etc/cups/cupsd.conf contains the following on line 8:```
BrowseAddress @LOCAL
```Here is my /etc/cups/cupsd.conf file:```
LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
Browsing On
BrowseAddress @LOCAL
BrowseLocalProtocols dnssd
DefaultAuthType Basic
<Location />
  # Allow remote access...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUis PS-Set-Default>
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
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
LogLevel warn
LogLevel warn
```I'm not sure whether any of the warnings would slow things down.  Would it be appropriate to delete the printer and redefine it?  I suppose I am asking two questions: (1) if I delete the printer and redefine it, will that create a new cupsd.conf, and (2)  is that likely to solve the problem given the messages that have been appearing in the log?

The access log for the same period as the error log shows how long it was taking to print each page.  I was manually duplexing the pages, so each job represents a page.  I do this frequently, so there was very little time lost between printing each page, probably less than 5 seconds.  Here's the access log:```
localhost - - [12/Oct/2015:23:48:02 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 27704 Print-Job successful-ok
localhost - - [12/Oct/2015:23:49:00 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 28071 Print-Job successful-ok
localhost - - [12/Oct/2015:23:50:11 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 27429 Print-Job successful-ok
localhost - - [12/Oct/2015:23:51:20 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 29139 Print-Job successful-ok
localhost - - [12/Oct/2015:23:52:49 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 31600 Print-Job successful-ok
localhost - - [12/Oct/2015:23:53:55 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 31344 Print-Job successful-ok
localhost - - [12/Oct/2015:23:55:54 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 31737 Print-Job successful-ok
localhost - - [12/Oct/2015:23:56:57 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24078 Print-Job successful-ok
localhost - - [12/Oct/2015:23:58:46 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24162 Print-Job successful-ok
localhost - - [13/Oct/2015:00:00:16 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 32884 Print-Job successful-ok
localhost - - [13/Oct/2015:00:01:23 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 29034 Print-Job successful-ok
localhost - - [13/Oct/2015:00:02:15 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24557 Print-Job successful-ok
localhost - - [13/Oct/2015:00:03:57 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24494 Print-Job successful-ok
localhost - - [13/Oct/2015:00:05:41 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24651 Print-Job successful-ok
localhost - - [13/Oct/2015:00:07:37 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 30028 Print-Job successful-ok
localhost - - [13/Oct/2015:00:09:03 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25303 Print-Job successful-ok
localhost - - [13/Oct/2015:00:11:06 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25584 Print-Job successful-ok
localhost - - [13/Oct/2015:00:12:27 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24277 Print-Job successful-ok
localhost - - [13/Oct/2015:00:14:06 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25812 Print-Job successful-ok
localhost - - [13/Oct/2015:00:16:13 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24259 Print-Job successful-ok
localhost - - [13/Oct/2015:00:18:21 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 27707 Print-Job successful-ok
localhost - - [13/Oct/2015:00:19:54 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 30332 Print-Job successful-ok
localhost - - [13/Oct/2015:00:21:28 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24359 Print-Job successful-ok
localhost - - [13/Oct/2015:00:23:01 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 19705 Print-Job successful-ok
localhost - - [13/Oct/2015:00:24:18 -0400] "POST / HTTP/1.1" 200 253 Create-Printer-Subscriptions successful-ok
localhost - - [13/Oct/2015:00:24:56 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24791 Print-Job successful-ok
localhost - - [13/Oct/2015:00:27:24 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24299 Print-Job successful-ok
localhost - - [13/Oct/2015:00:28:16 -0400] "POST / HTTP/1.1" 200 153 Cancel-Subscription successful-ok
localhost - - [13/Oct/2015:00:28:40 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25634 Print-Job successful-ok
localhost - - [13/Oct/2015:00:29:48 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 29303 Print-Job successful-ok
localhost - - [13/Oct/2015:00:33:24 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25177 Print-Job successful-ok
localhost - - [13/Oct/2015:00:39:32 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 27514 Print-Job successful-ok
localhost - - [13/Oct/2015:00:41:42 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25117 Print-Job successful-ok
localhost - - [13/Oct/2015:00:47:46 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 34703 Print-Job successful-ok
localhost - - [13/Oct/2015:00:50:33 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 31221 Print-Job successful-ok
localhost - - [13/Oct/2015:00:53:22 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 26664 Print-Job successful-ok
localhost - - [13/Oct/2015:00:54:39 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24890 Print-Job successful-ok
localhost - - [13/Oct/2015:00:59:15 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 23965 Print-Job successful-ok
localhost - - [13/Oct/2015:01:05:14 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25158 Print-Job successful-ok
localhost - - [13/Oct/2015:01:08:10 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 23698 Print-Job successful-ok
localhost - - [13/Oct/2015:01:10:14 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25926 Print-Job successful-ok
localhost - - [13/Oct/2015:01:12:27 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 25818 Print-Job successful-ok
localhost - - [13/Oct/2015:01:18:46 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 29194 Print-Job successful-ok
localhost - - [13/Oct/2015:01:24:10 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 24037 Print-Job successful-ok
localhost - - [13/Oct/2015:01:26:46 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 33302 Print-Job successful-ok
localhost - - [13/Oct/2015:01:30:50 -0400] "POST /printers/Deskjet_9800 HTTP/1.1" 200 27953 Print-Job successful-ok
```

There are no changes other than the issue I initially quoted in the first post.  I have always used HPLIP, the printer is connected via USB, neither the program or the OS has been recently upgraded to a new release, and the print quality is set to normal.

Sorry about the slow reply, I was out of town for a few days.  Thanks for your help to date.

---

### Post by tgalati4 on 2015-10-17
As a general rule, whenever you upgrade your kernel, you need to delete your printers and reinstall them.  Try that and see if printing improves.

---

### Post by cscj01 on 2015-10-19
Well, I deleted the printer and redefined it.  Same problem.  Is there something else I should delete when deleting the printer?  I got no errors when printing a full page document, but here is the error log with a number of warnings.  Should I be looking at any of those?```
W [18/Oct/2015:07:39:00 -0400] No limit for Validate-Job defined in policy default and no suitable template found.
W [18/Oct/2015:07:39:00 -0400] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [18/Oct/2015:07:39:00 -0400] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [18/Oct/2015:07:39:00 -0400] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [18/Oct/2015:07:39:00 -0400] No JobPrivateAccess defined in policy default - using defaults.
W [18/Oct/2015:07:39:00 -0400] No JobPrivateValues defined in policy default - using defaults.
W [18/Oct/2015:07:39:00 -0400] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [18/Oct/2015:07:39:00 -0400] No SubscriptionPrivateValues defined in policy default - using defaults.
W [18/Oct/2015:07:39:00 -0400] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.
W [18/Oct/2015:07:39:00 -0400] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [18/Oct/2015:07:39:00 -0400] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [18/Oct/2015:07:39:00 -0400] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [18/Oct/2015:07:39:00 -0400] No JobPrivateAccess defined in policy authenticated - using defaults.
W [18/Oct/2015:07:39:00 -0400] No JobPrivateValues defined in policy authenticated - using defaults.
W [18/Oct/2015:07:39:00 -0400] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [18/Oct/2015:07:39:00 -0400] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
```

---

### Post by tgalati4 on 2015-10-19
Those are default warnings.  If you have a lot of users printing, then you may set up some policies, but otherwise,  I would look at the printer itself.  Can you print from Windows?  There are a lot of sensors on the printer and if one of them is not working, then you get erratic behavior.  Plug it into a Windows computer and print your large document.  If you get the same problem then it is not a CUPS problem but an HP printer problem.

---

### Post by cscj01 on 2015-10-22
It seems to be the printer.  So I'll close this because I've purchased an Epson Artisan 1430.  Thanks for the help.

---


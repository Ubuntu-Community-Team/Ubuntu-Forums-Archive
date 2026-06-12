---
title: "Local Print OK but Network Print Fails, job completed in CUPS but no printout"
date: 2008-08-16
forum: General Help
---

### Post by spherics on 2008-08-16
Help please

I have a HP Office Jet 5610 printer installed on Ubuntu Desktop 8.04LTS.  I can print to it from the local Desktop no problem.  I can print the Test Page from the local Desktop no problem.

I have shared the printer in Ubuntu and can access it from a WinXP machine.  However when I print to it from WinXP, CUPS shows the job has completed but no output appears on the printer.

Also if I print the Test Page from WinXP CUPS shows the job has completed but no output appears on the printer.  

There is no action at the printer at all when printing from WinXP.  It seems like CUPS is receiving the print job over the network ok, saying the job is complete, but is not actually sending it to the printer.

I'm new to Ubuntu so I'd really appreciate some help please.  I have searched through the forums but have not found anything that helps.

I have included some of the log file output below.  The only thing I can see is "DNSServiceRegister failed with error -65537" but I don't know if that is significant or not.


Regards, Spherics


CUPS Show Completed Jobs
========================
Officejet_5600_series-15  	Test Page  	Admin  	97k  	1  	completed at Sat 16 Aug 2008 13:49:04 BST


Access Log
==========
localhost - - [16/Aug/2008:13:49:04 +0100] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.0.2 - - [16/Aug/2008:13:49:04 +0100] "POST /printers/Officejet_5600_series HTTP/1.1" 200 112492 Print-Job 

successful-ok


Error Log
=========
E [16/Aug/2008:12:59:54 +0100] DNSServiceRegister failed with error -65537
E [16/Aug/2008:12:59:54 +0100] DNSServiceRegister failed with error -65537

---

### Post by spherics on 2008-08-17
I'd really appreciate some help on this please guys

---

### Post by spherics on 2008-08-18
No feedback, not even one.

Can anyone confirm that CUPS works on UD 8.04LTS ?

---

### Post by spherics on 2008-09-16
bump

---

### Post by spherics on 2008-09-17
bump

---

### Post by lil_elvis2000 on 2008-09-17
Be handy if you could tell us version numbers (Im guessing 1.3.7) and are you using cups client on WIndows. Plus a look at your cupsd.conf and printers.conf would also help.

I've successfully used CUPS via SAMBA for a while now.

---

### Post by spherics on 2008-09-18
Thanks for the response

Versions are, Ubuntu Desktop 8.04LTS and Cups 1.3.7

>are you using cups client on WIndows

Don't know what Windows calls the client end, but I added the printer using the Windows Add Printer Wizard and specified an Internet printer with the URL of the printer on the Ubuntu box.  I.E. [http://192.168.0.40:631/printers/Officejet_5600_series](http://192.168.0.40:631/printers/Officejet_5600_series).  So I think that means Windows is talking to the Ubuntu box using the IPP protocol that CUPS supports and not a Samba share.

>a look at your cupsd.conf and printers.conf would also help.

Files attached below.

Also a note on how I got to this point in case I missed anything.

I installed Ubuntu.

I installed a HP 5610 USB printer on the Ubuntu box (plugged it in and some scripts ran automatically to install it).  I can print to the printer from the Ubuntu desktop.

I then Shared a folder (Right Click > Properties > Share > Share This Folder) which kicked off some scripts and installed Samba.  I can see the shares on the Ubuntu box from an XPHome box and read and write files to the share.

I then shared the printer with these steps

(System > Administration > Printing > Server Settings > Share Published Printers)

(System > Administration > Printing > Server Settings > Allow Printing From The Internet)

(System > Administration > Printing > Officjet_5600 > Policies > Shared)

which kicked off some scripts and installed CUPS.

I added the printer on my XPHome box using the Windows Add Printer Wizard and specified an Internet printer.  I can now see the printer from XP and send print jobs to it.  The jobs appear in the CUPS log, and show as printed, but never actually reach the printer.

Is there some step I have omitted in the above ?

Conf files below



cupsd.conf

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  Allow all
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Allow all
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Allow all
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
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
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

printers.conf

# Printer configuration file for CUPS v1.3.7
# Written by cupsd on 2008-09-16 17:40
<Printer Officejet_5600_series>
Info HP Officejet 5600 series
DeviceURI hp:/usb/Officejet_5600_series?serial=CN6BND71GS04B2
State Idle
StateTime 1221583203
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer Officejet_5600_series_fax>
Info Fax queue for HP Officejet 5600 series
DeviceURI hpfax:/usb/Officejet_5600_series?serial=CN6BND71GS04B2
State Idle
StateTime 1221583203
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer PDF>
Info PDF
DeviceURI cups-pdf:/
State Idle
StateTime 1214994123
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by spherics on 2008-09-20
bump

---

### Post by spherics on 2008-09-22
bump

---

### Post by spherics on 2008-09-23
bump

---

### Post by lovi9573 on 2008-09-24
Hey,

I'm right with you.  I have exactly the same problem.  Print jobs are sent from XP machine over network to IPP address of cups.  They appear to be completed according to cups but nothing comes out of the printer.  Prints locally just fine.  I have not found a solution yet, but WHEN I do I will post.  Hopefully that is sooner rather than later

---

### Post by lovi9573 on 2008-09-24
So,
That took me all of about 15 minutes :) after having worked on this for days.
It appears (and anyone can shoot me down for this if they want) that having my printer driver on the xp machine and on the linux machine was the problem.  The data, after having gone through the xp driver, was unintelligible to the cups printer driver which was setup to accept raw data.  So it would accept the "raw" do nothing with it, and obediently call it complete.

Fix: (hopefully this will work for you) I changed my printer driver from the proper one for my printer to "Generic: MS Publisher Imagesetter" which apparently sends out postscipt output that the cups driver will actually do something with.

Good Luck.

---

### Post by spherics on 2008-09-24
Yep, changed to Generic: MS Publisher Color Printer and it works for me too.  Thanks.

It would be nice if CUPS reported the job status more correctly.

There is something about CUPS having printer filters for the printer type which I haven't understood yet.  Perhaps the problem is it doesn't have a filter for the HP Officejet printer language.

---


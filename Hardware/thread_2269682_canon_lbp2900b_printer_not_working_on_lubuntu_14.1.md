---
title: "canon lbp2900b printer not working on lubuntu 14.10"
date: 2015-03-17
forum: Hardware
---

### Post by pramod5 on 2015-03-17
I have installed Drivers

Linux_CAPT_PrinterDriver_V260_uk_EN

ndrvcups-common_2.60-1_i386.deb
cndrvcups-capt_2.60-1_i386.deb

Printer Succefully added but still not able to print

when try to Print Self Test Page shows message

**There was a problem connecting to cups server**

I have attached cups file

Please help !!!

Pramod

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
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

#
#

---

### Post by pdc on 2015-03-17
this looks awfully like a thread that was started a week ago by someone using the name prem_333

[http://ubuntuforums.org/showthread.php?t=2268076&highlight=canon](http://ubuntuforums.org/showthread.php?t=2268076&highlight=canon)

.......LBP2900..............lubuntu 14.10 

I posted a reply there: please check it out; please ask for more help; as you feel you need it; after you have read the above reply

---

### Post by pramod5 on 2015-03-18
when I use 
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59687 &#8211;E

It Gives Message..

**lpadmin: Unknown argument "name]"**

what to do???

---

### Post by pdc on 2015-03-18
.........hmmmmmmmmmmmmm...

I copied the commands from a Canon CAPT install guide; .....my error...............with ubuntu, one needs a different port so can I suggest

```
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 &#8211;E
```

.....the error message is saying > lpadmin: Unknown argument "name]" so I see you call the printer LBP2900B ...........so can you paste this command into a terminal please ```
/usr/sbin/lpinfo -v
``` and if you can paste the result back here to check we are using the correct name .........but do try the above command 

_____________

do you just have one printer, the LBP2900, connected by usb? I ask that because to register it with the ccpd daemon, one calls it > /dev/usb/lp0        convention is first printer is lp_zero; second printer is lp_one etc

---

### Post by pramod5 on 2015-03-18
results as below

mark@mark-MS-7211:~$ /usr/sbin/lpinfo -v
network ipp14
direct ccp
network socket
network ipp
network lpd
direct parallel:/dev/lp0
network ipps
network http
network https
serial serial:/dev/ttyS0?baud=115200
direct usb://Canon/LBP2900?serial=0000A362MB6V
network smb
mark@mark-MS-7211:~$

---

### Post by pramod5 on 2015-03-18
i have only one printer connected to usb

---

### Post by pramod5 on 2015-03-18
mark@mark-MS-7211:~$ /dev/usb/lp0 
bash: /dev/usb/lp0: Permission denied
mark@mark-MS-7211:~$

---

### Post by pdc on 2015-03-18
thanks for the info; **that all seems fine**:

............ have you already tried to set up the printer: ie if you open the PRINTERS box, does it show some sort of reference to an LBP2900? If so, I would suggest deleting it and then doing the code that was in my last post: 

```
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 –E
```

and after that, the cppd daemon registration ```
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0
```
____________

that should put everything in place: one then restarts the ccpd daemon with ```
sudo /etc/init.d/ccpd start
``` and you can check it with ```
captstatusui -P LBP2900
``` and if you get two numbers back, try to print something

............am I correct that you have a 32bit ubuntu please?

---

### Post by pramod5 on 2015-03-18
mark@mark-MS-7211:~$ sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 &#8211;E
sudo: unable to resolve host mark-MS-7211
[sudo] password for mark: 
lpadmin: Unknown argument "&#8211;E".
mark@mark-MS-7211:~$ sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 &#8211;E
sudo: unable to resolve host mark-MS-7211
lpadmin: Unknown argument "&#8211;E".
mark@mark-MS-7211:~$

---

### Post by pramod5 on 2015-03-18
:rolleyes::rolleyes::rolleyes::frown::frown::frown:

---

### Post by pramod5 on 2015-03-18
Please Help Someone,....

---

### Post by pdc on 2015-03-18
..........there is something strange with your system; 

for many of us, we use Google when we have something we do not know; 

> sudo unable to resolve host

I googled on this ............ have a read at this [http://askubuntu.com/questions/59458/unable-to-resolve-host-none](http://askubuntu.com/questions/59458/unable-to-resolve-host-none)            (I think you need to get your system behaving normally; before installing a printer)

the thread I show above suggests you read the file that is called hostname that lives in the /etc directlry; you read it by using the command ```
gedit /etc/hostname
``` and if you want to change it, you close the file and re-open it with sudo powers by pasting ```
gksudo gedit /etc/hostname
```

---


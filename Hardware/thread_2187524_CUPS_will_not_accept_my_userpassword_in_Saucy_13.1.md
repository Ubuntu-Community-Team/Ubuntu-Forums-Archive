---
title: "CUPS will not accept my user/password in Saucy 13.10"
date: 2013-11-12
forum: Hardware
---

### Post by kernelles on 2013-11-12
I have used Ubuntu for years, upgrading every 6 months, and never had this issue before. When I go to localhost:631, CUPS admin page displays, but when I try to make admin changes, such as modify a printer, it prompts for user and password, as usual, but will not accept my credentials. I have tried:

1. Logging out of Ubuntu and back in again
2. Clearing browser cookies & cache
3. Captilized & non versions of my user name
4. Entering these commands in terminal: 
sudo usermod -aG lpadmin <username>
sudo /etc/init.d/cups restart

There are no other users on this machine, mine is the only account, and I do have admin privileges.

Thanks,

Les.

---

### Post by zKhtdyX on 2013-11-12
What is the content of your /etc/cups/cupsd.conf ?

---

### Post by coffeecat on 2013-11-13
A slightly long shot here, because this should only be relevant if you have had to install the gksu package, but open a terminal and run:

```
gksu-properties
```

If the authentication mode is set to su, change it to sudo and try the CUPS admin page again.

---

### Post by kernelles on 2013-11-13
> **zKhtdyX said:**
> What is the content of your /etc/cups/cupsd.conf ?

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
#

---

### Post by kernelles on 2013-11-13
> **coffeecat said:**
> A slightly long shot here, because this should only be relevant if you have had to install the gksu package, but open a terminal and run:

```
gksu-properties
```

If the authentication mode is set to su, change it to sudo and try the CUPS admin page again.

Thanks....it was set to sudo already.

---

### Post by zKhtdyX on 2013-11-13
hmm, the only difference between your config file and the default one in ubuntu 12.04 is the missing directive "SystemGroup lpadmin" but this was already not used any more in 12.04.
 When you are in lpadmin group you should be able to add printer etc. Nobody experiencing the same issue with 13.10?

---

### Post by kernelles on 2013-11-14
> **zKhtdyX said:**
> hmm, the only difference between your config file and the default one in ubuntu 12.04 is the missing directive "SystemGroup lpadmin" but this was already not used any more in 12.04.
 When you are in lpadmin group you should be able to add printer etc. Nobody experiencing the same issue with 13.10?

I can't find anyone else experiencing the same problem. I also have 13.10 on another machine, and I can access cups admin no problem on that one. Any ideas?

---

### Post by allanmitch on 2013-11-15
I have the same problem.  I upgraded from 13.04 to 13.10 and now I'm unable to log into the cups web administrator interface.  In the past I've just been able to enter my user/password.

---

### Post by allanmitch on 2013-11-15
Please check out:
[http://www.ubuntuupdates.org/package/core/saucy/main/proposed/cups](http://www.ubuntuupdates.org/package/core/saucy/main/proposed/cups)
Is this our problem?

---

### Post by kernelles on 2013-11-15
> **allanmitch said:**
> Please check out:
[http://www.ubuntuupdates.org/package/core/saucy/main/proposed/cups](http://www.ubuntuupdates.org/package/core/saucy/main/proposed/cups)
Is this our problem?

Not sure, as I only had time to look at it your link briefly. Mine is working intermittently now, but I have to keep rebooting for that to happen. I do notice that the version of cups that is installed on my system is a release candidate, which is odd. Let me know if you find anything. 

Cheers,
Les.

---

### Post by nluetic on 2014-01-02
Sounds I had the same problem:

While trying to find an error with pdf printing I reconfigured and restarted cups several times. When trying to access the webinterface my login was denied, although user/credentials were correct and the user was in the group lpadmin, as required.

After some experimenting, I found out, that restarting cups with

[FONT=fixedsys]sudo /etc/init.d/cups restart[/FONT]

left several cupsd processes running. 

When killing just all of them with

[FONT=fixedsys]sudo killall cupsd[/FONT]

cups was restarted automatically and login was again possible.

At least, that way you don't have to reboot ...

---

### Post by tartley on 2014-01-23
I have the same issue. Brand new install of 13.10.

nluetic's advice to "sudo killall cupsd" (followed by sudo /etc/init.d/cups start) doesn't seem to help.

Presumably there's something I still have to edit before restarting those processes. Will post if I figure it.

---

### Post by tartley on 2014-01-23
I realised that I don't need CUPS web interface. I instead opened up the Ubuntu native 'Printers' config app. It already had my printer added there, but it was not selected as 'default' (no green check) and trying to print to it didn't work (errors or unexpected exit, depending on the application). However, I was able to delete this printer and add a new one, which went smoothly (unlike my initial attempts before I'd installed the correct driver .deb files from the Brother site.)

This newly installed printer works great. My problem solved.

---

### Post by BZFlagLEGOManiac on 2014-08-16
I've just had this same problem on a fresh install.

The solution:

- from a terminal prompt -

sudo lppasswd -a username

Enter the user's password for sudo, then enter the CUPS password you want to use, then:

sudo service cups restart


- In a web browser -

In the address bar, enter:

[http://localhost:631/](http://localhost:631/)

And add your printer(s), providing the username and CUPS password used earlier.

---


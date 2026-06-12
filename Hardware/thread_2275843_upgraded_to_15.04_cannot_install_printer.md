---
title: "upgraded to 15.04 cannot install printer"
date: 2015-04-28
forum: Hardware
---

### Post by Peter cooke on 2015-04-28
I installed ubuntu 15.04 and i cant install a printer. it keeps saying cups failed to connect to server.. What am i doing wrong. worker ok with 14

---

### Post by ian-weisser on 2015-04-29
Is CUPS running?
Can you open the cups web page at [http://localhost:631](http://localhost:631) ?

---

### Post by Peter cooke on 2015-04-30
no the page does not open

---

### Post by ian-weisser on 2015-04-30
Then CUPS is not running. That's why you cannot connect to it.

Open a terminal and try the following command:
```
sudo service cups restart
```

The system will ask for your password. Enter it.

If there is an error message, please copy-and-paste all messages here.
If there is no error message (indeed,no feedback at all), then try the web page again, and try printing.

---

### Post by Peter cooke on 2015-04-30
the page does not open how do you check cups is running

There was an error during the CUPS operation: 'failed to connect to server'.I did that still the same. I clicked prrinters in system settings. box came up Printers-localhost. I clicked connect. another box with localhost as the server clicked connect. CPS server error.what have i done wron or is it the cups playing up

the printer box says print to file generic printer still cant print tried to install the printer and got the following There was an error during the CUPS operation: 'failed to connect to  server'.I did that still the same. I clicked prrinters in system  settings. box came up Printers-localhost. I clicked connect. another box  with localhost as the server clicked connect. CPS server error.what  have i done wron or is it the cups playing up

tried sudo service cups restart no errors tried printing only print to file available. still cant open the page  [http://localhost:631](http://localhost:631)

I have now purged CUPS and re instaklled it . You guessed it I STILL CANT INSTALL MY PRINTER!! all I get is There was an error during the CUPS operation: 'failed to connect to server'. and I have tried starting cups still nothing.

Has anyone got the answer??

---

### Post by ian-weisser on 2015-05-06
Do you have a file /var/log/cups/error_log ?
If so, please post the contents here.

---

### Post by Peter cooke on 2015-05-06
> **ian-weisser said:**
> Do you have a file /var/log/cups/error_log ?
If so, please post the contents here.

W [05/May/2015:07:57:51 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [05/May/2015:07:57:51 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [05/May/2015:07:57:51 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [05/May/2015:07:57:51 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [05/May/2015:07:57:51 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [05/May/2015:21:03:49 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [05/May/2015:21:03:49 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [05/May/2015:21:03:50 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [05/May/2015:21:03:50 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [05/May/2015:21:03:50 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [05/May/2015:21:10:06 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [05/May/2015:21:10:06 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [05/May/2015:21:10:06 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [05/May/2015:21:10:06 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [05/May/2015:21:10:06 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [05/May/2015:22:10:56 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [05/May/2015:22:10:56 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [05/May/2015:22:10:56 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [05/May/2015:22:10:56 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [05/May/2015:22:10:56 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [05/May/2015:23:46:11 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [05/May/2015:23:46:11 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [05/May/2015:23:46:11 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [05/May/2015:23:46:11 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [05/May/2015:23:46:11 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [06/May/2015:00:26:42 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [06/May/2015:00:26:42 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [06/May/2015:00:26:42 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [06/May/2015:00:26:42 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [06/May/2015:00:26:42 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [06/May/2015:08:39:06 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [06/May/2015:08:39:06 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [06/May/2015:08:39:06 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [06/May/2015:08:39:06 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [06/May/2015:08:39:06 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.





my usb is also playing up my dongle will only read not write as it used to

kind regards

peter

---

### Post by ian-weisser on 2015-05-06
Hmmm. Please show us lines 80-90 of /etc/cups/cupsd.conf

---

### Post by Peter cooke on 2015-05-07
> **ian-weisser said:**
> Hmmm. Please show us lines 80-90 of /etc/cups/cupsd.conf

how do I open the file

---

### Post by ian-weisser on 2015-05-07
You can use the '+ Reply to Thread' button to expose the 'attach a file' option, and simply attach the entire file. It's usually not a large file.

Or you can easily open the file in gedit (or any text editor). It's just a text file. Copy-and-paste the contents. Use [code] tags on the forums to keep formatting.

---

### Post by Peter cooke on 2015-05-07
> **ian-weisser said:**
> You can use the '+ Reply to Thread' button to expose the 'attach a file' option, and simply attach the entire file. It's usually not a large file.

Or you can easily open the file in gedit (or any text editor). It's just a text file. Copy-and-paste the contents. Use [code] tags on the forums to keep formatting.


I hope the files are attached if not i will try tonight

> **Peter cooke said:**
> I hope the files are attached if not i will try tonight

I have tried to open the file and tried to attach it to a message when I try to open it I get  you do not have the permissions nessasary  and I also have a file named   cups,conf 0 both have a box with a X in it I have signed in as the admin. I rely need the printer as work is backing up

---

### Post by ian-weisser on 2015-05-09
Well, we'll certainly try to help...but we don't have much to work with yet.


Please show us the output of the following command:
```
ls -l /etc/cups
```

For example, here's what mine looks like:
```
$ ls -l /etc/cups
total 64
-rw------- 1 root lp    108 Mar 26 16:13 classes.conf
-rw-r----- 1 root lp    108 Mar 26 16:08 classes.conf.O
-rw-r--r-- 1 root root 2830 Apr  9 23:04 cups-browsed.conf
**-rw-r--r-- 1 root root 4500 Oct 22  2014 cupsd.conf**
-rw-r--r-- 1 root root 2931 Feb 14 05:26 cups-files.conf
drwxr-xr-x 2 root root 4096 Oct 16  2014 interfaces
drwxr-xr-x 2 root lp   4096 May  2 20:27 ppd
-rw------- 1 root lp   2317 May  8 12:32 printers.conf
-rw------- 1 root lp   2497 May  8 09:11 printers.conf.O
-rw-r--r-- 1 root root  240 Oct 22  2014 raw.convs
-rw-r--r-- 1 root root  211 Oct 22  2014 raw.types
-rw-r--r-- 1 root root  142 Feb 14 05:26 snmp.conf
drwx------ 2 root lp   4096 Oct 22  2014 ssl
-rw-r----- 1 root lp    385 May  8 22:59 subscriptions.conf
-rw-r----- 1 root lp    537 May  8 12:32 subscriptions.conf.O

```
-rw-r--r-- means everyone can read the file, but only root can write to it.That's the correct permission for the cupsd.conf file.
Let's see if yours is different.



Here's an example of how I would look at lines 80-90 of the /etc/cups/cupsd.conf file using the 'head' and 'tail' commands to narrow down to the section we care about:
```
$ head -n 96 /etc/cups/cupsd.conf | tail -n 9

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

```

You can view the content any way you wish (nano, cat, less, head, tail, etc.)
I merely want to know whether that section says 'default' like mine,or something different.

---

### Post by Peter cooke on 2015-05-09
peter@peter-GA-970A-DS3:~$ ls -l /etc/cups
total 64
-rw------- 1 root lp    108 Jan 12 09:46 classes.conf
-rw-r--r-- 1 root root 2830 Apr 10 05:05 cups-browsed.conf
-rw-r----- 1 root lp   3203 Feb 11 21:19 cupsd.conf
-rw-r----- 1 root lp   3244 Feb 11 21:19 cupsd.conf.O
-rw-r----- 1 root lp    374 Feb 11 21:19 cupsd-systemd-listen.conf.O
-rw-r--r-- 1 root root 2931 Feb 14 11:27 cups-files.conf
drwxr-xr-x 2 root root 4096 Feb 14 11:27 interfaces
drwxr-xr-x 2 root lp   4096 Feb 14 11:27 ppd
-rw------- 1 root lp    623 May  6 19:11 printers.conf
-rw------- 1 root lp    623 Apr 25 13:19 printers.conf.O
-rw-r--r-- 1 root root  240 May  6 19:14 raw.convs
-rw-r--r-- 1 root root  211 May  6 19:14 raw.types
-rw-r--r-- 1 root root  142 Feb 14 11:27 snmp.conf
drwx------ 2 root lp   4096 Oct 22  2014 ssl
-rw-r----- 1 root lp     91 Apr 26 13:11 subscriptions.conf
-rw-r----- 1 root lp    231 Apr 25 13:11 subscriptions.conf.O


$ head -n 96 /etc/cups/cupsd.conf | tail -n 9
head: cannot open &#8216;/etc/cups/cupsd.conf&#8217; for reading: Permission denied

---

### Post by Peter cooke on 2015-05-09
> **ian-weisser said:**
> Well, we'll certainly try to help...but we don't have much to work with yet.


Please show us the output of the following command:
```
ls -l /etc/cups
```

For example, here's what mine looks like:
```
$ ls -l /etc/cups
total 64
-rw------- 1 root lp    108 Mar 26 16:13 classes.conf
-rw-r----- 1 root lp    108 Mar 26 16:08 classes.conf.O
-rw-r--r-- 1 root root 2830 Apr  9 23:04 cups-browsed.conf
**-rw-r--r-- 1 root root 4500 Oct 22  2014 cupsd.conf**
-rw-r--r-- 1 root root 2931 Feb 14 05:26 cups-files.conf
drwxr-xr-x 2 root root 4096 Oct 16  2014 interfaces
drwxr-xr-x 2 root lp   4096 May  2 20:27 ppd
-rw------- 1 root lp   2317 May  8 12:32 printers.conf
-rw------- 1 root lp   2497 May  8 09:11 printers.conf.O
-rw-r--r-- 1 root root  240 Oct 22  2014 raw.convs
-rw-r--r-- 1 root root  211 Oct 22  2014 raw.types
-rw-r--r-- 1 root root  142 Feb 14 05:26 snmp.conf
drwx------ 2 root lp   4096 Oct 22  2014 ssl
-rw-r----- 1 root lp    385 May  8 22:59 subscriptions.conf
-rw-r----- 1 root lp    537 May  8 12:32 subscriptions.conf.O

```
-rw-r--r-- means everyone can read the file, but only root can write to it.That's the correct permission for the cupsd.conf file.
Let's see if yours is different.



Here's an example of how I would look at lines 80-90 of the /etc/cups/cupsd.conf file using the 'head' and 'tail' commands to narrow down to the section we care about:
```
$ head -n 96 /etc/cups/cupsd.conf | tail -n 9

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

```

You can view the content any way you wish (nano, cat, less, head, tail, etc.)
I merely want to know whether that section says 'default' like mine,or something different.

peter@peter-GA-970A-DS3:~$ ls -l /etc/cups
total 64
-rw------- 1 root lp    108 Jan 12 09:46 classes.conf
-rw-r--r-- 1 root root 2830 Apr 10 05:05 cups-browsed.conf
-rw-r----- 1 root lp   3203 Feb 11 21:19 cupsd.conf
-rw-r----- 1 root lp   3244 Feb 11 21:19 cupsd.conf.O
-rw-r----- 1 root lp    374 Feb 11 21:19 cupsd-systemd-listen.conf.O
-rw-r--r-- 1 root root 2931 Feb 14 11:27 cups-files.conf
drwxr-xr-x 2 root root 4096 Feb 14 11:27 interfaces
drwxr-xr-x 2 root lp   4096 Feb 14 11:27 ppd
-rw------- 1 root lp    623 May  6 19:11 printers.conf
-rw------- 1 root lp    623 Apr 25 13:19 printers.conf.O
-rw-r--r-- 1 root root  240 May  6 19:14 raw.convs
-rw-r--r-- 1 root root  211 May  6 19:14 raw.types
-rw-r--r-- 1 root root  142 Feb 14 11:27 snmp.conf
drwx------ 2 root lp   4096 Oct 22  2014 ssl
-rw-r----- 1 root lp     91 Apr 26 13:11 subscriptions.conf
-rw-r----- 1 root lp    231 Apr 25 13:11 subscriptions.conf.O


$ head -n 96 /etc/cups/cupsd.conf | tail -n 9
head: cannot open ‘/etc/cups/cupsd.conf’ for reading: Permission denied

---

### Post by ian-weisser on 2015-05-09
Yes, your permissions are different, for some odd reason.

The following commands will create a copy of the file in /tmp that you should be able to open, and should be able to attach here.
```
sudo cp /etc/cups/cupsd.conf /tmp/cupsd.conf.copy
sudo chmod +r /tmp/cupsd.conf.copy
```

If the cause of your problem is similar to [https://bugzilla.redhat.com/show_bug.cgi?id=1141154](https://bugzilla.redhat.com/show_bug.cgi?id=1141154) , then the fix will be easy.

---

### Post by Peter cooke on 2015-05-10
> **ian-weisser said:**
> Yes, your permissions are different, for some odd reason.

The following commands will create a copy of the file in /tmp that you should be able to open, and should be able to attach here.
```
sudo cp /etc/cups/cupsd.conf /tmp/cupsd.conf.copy
sudo chmod +r /tmp/cupsd.conf.copy
```

If the cause of your problem is similar to [https://bugzilla.redhat.com/show_bug.cgi?id=1141154](https://bugzilla.redhat.com/show_bug.cgi?id=1141154) , then the fix will be easy.
```

  	 	 	 	   LogLevel warn
MaxLogSize 0
Listen /var/run/cups/cups.sock
Listen /var/run/cups/cups.sock
Browsing Off
BrowseLocalProtocols dnssd
DefaultAuthType Basic
WebInterface Yes
<Location />
  Order allow,deny
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
JobPrivateAccess default
JobPrivateValues default
SubscriptionPrivateAccess default
SubscriptionPrivateValues default
```

---

### Post by ian-weisser on 2015-05-10
> **Peter cooke said:**
> ```

  [...]
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  [...]
</Policy>
[B]JobPrivateAccess default
JobPrivateValues default
SubscriptionPrivateAccess default
SubscriptionPrivateValues default[/B]
```

Well, there's something different.
You have a whole set of duplicated policies...outside the <Policy> tag.
Delete the bottom set.

Use nano (not gedit) to edit this root-owned file.
```
sudo nano /etc/cups/cupsd.conf
```
Use CTRL+X to save and exit when your edit is complete.

---

### Post by Peter cooke on 2015-05-11
> **ian-weisser said:**
> Well, there's something different.
You have a whole set of duplicated policies...outside the <Policy> tag.
Delete the bottom set.

Use nano (not gedit) to edit this root-owned file.
```
sudo nano /etc/cups/cupsd.conf
```
Use CTRL+X to save and exit when your edit is complete.

sorry that made no differance still the same result. shaould we delete cups and re install?

---

### Post by ian-weisser on 2015-05-11
I thought you already deleted CUPS and reinstalled...
Did you restart cups to load the changed config?

---

### Post by Peter cooke on 2015-05-13
> **ian-weisser said:**
> I thought you already deleted CUPS and reinstalled...
Did you restart cups to load the changed config?

yes I did restart cups but it still will not install

---

### Post by ian-weisser on 2015-05-13
'[...]will not install'?
Do you have the same problem (same error log), or a different problem now?

The problem you described was that CUPS would install, but the cupsd server failed.
Please be clear. We cannot see what you are experiencing.

---

### Post by hasselkuss on 2015-05-14
Hi,
 I had the same problems after upgrading to Ubuntu 15.04. My cupsd.conf file had the same erroneous issues as yours.
In the meantime I solved the problem after investigating the warning in the file /var/log/cups/error_log  
 ```
 W [06/May/2015:08:39:06 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
```
 The relevant lines are located directly at the beginning of the cupsd.conf file starting with „Listen ...“
 From your submitted code segment I saw your cupsd.conf looked the same.
 
 How to correct:
 Edit the cupsd.conf file
 ```
sudo nano /etc/cups/cupsd.conf
```
 
 Replace the first appearance of “Listen /var/run/cups/cups.sock” (should be in line 3)  
 ```

LogLevel warn
MaxLogSize 0
**Listen /var/run/cups/cups.sock**
Listen /var/run/cups/cups.sock
Browsing Off
...
```
 by “Listen localhost:631”
 
 Your cupsd.conf should then look like this
 ```
...
**Listen localhost:631**
Listen /var/run/cups/cups.sock
... 
```
  After saving the change with CTRL-X and restart of cups, my printer could be accessed and is working fine now.
 Hopefully this solves your problem too.

---

### Post by Peter cooke on 2015-05-14
> **hasselkuss said:**
> Hi,
 I had the same problems after upgrading to Ubuntu 15.04. My cupsd.conf file had the same erroneous issues as yours.
In the meantime I solved the problem after investigating the warning in the file /var/log/cups/error_log  
 ```
 W [06/May/2015:08:39:06 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
```
 The relevant lines are located directly at the beginning of the cupsd.conf file starting with „Listen ...“
 From your submitted code segment I saw your cupsd.conf looked the same.
 
 How to correct:
 Edit the cupsd.conf file
 ```
sudo nano /etc/cups/cupsd.conf
```
 
 Replace the first appearance of “Listen /var/run/cups/cups.sock” (should be in line 3)  
 ```

LogLevel warn
MaxLogSize 0
**Listen /var/run/cups/cups.sock**
Listen /var/run/cups/cups.sock
Browsing Off
...
```
 by “Listen localhost:631”
 
 Your cupsd.conf should then look like this
 ```
...
**Listen localhost:631**
Listen /var/run/cups/cups.sock
... 
```
  After saving the change with CTRL-X and restart of cups, my printer could be accessed and is working fine now.
 Hopefully this solves your problem too.

Thank you its been a while since I used the printer all works fine now..

---


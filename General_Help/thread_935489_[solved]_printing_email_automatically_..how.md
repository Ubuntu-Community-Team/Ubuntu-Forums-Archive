---
title: "[solved] printing email automatically ..how???"
date: 2008-10-01
forum: General Help
---

### Post by infotek on 2008-10-01
**Email to Printer Gateway**

Jason Ellison
[http://jasonellison.net/files/Email_to_printer_gateway.pdf](http://jasonellison.net/files/Email_to_printer_gateway.pdf)

I'm posting this here because I read an unanswered post describing exactly what I wanted to do. 

printing email automatically ..how???
[http://ubuntuforums.org/showthread.php?t=203556](http://ubuntuforums.org/showthread.php?t=203556)

 Well I did it and here is how...



This document covers setting up a Linux box to download email from a POP3 account on a Microsoft Exchange server and printing it to a network printer. When the emails are downloaded they are deleted. Already read emails are also deleted. Only new emails will be printed.

This example was done using Slackware 12.0.0 but it would work with a few changes on Ubuntu.

**Setup printer in cups**

chmod 755 /etc/rc.d/rc.cups
/etc/rc.d/rc.cups start
links [http://127.0.0.1:631/](http://127.0.0.1:631/)

add the printer, print a test page, and make it the default or specify it in the lpr command.


**Create user**

root@monitor:~# adduser
Login name for new user []: printemail
User ID ('UID') [ defaults to next available ]:
Initial group [ users ]:
Additional groups (comma separated) []:
Home directory [ /home/printemail ]
Shell [ /bin/bash ] /bin/false
- Warning: /bin/false is not in /etc/shells (potential problem using FTP)
Do you wish to change the shell ? (Y/n) n
Expiry date (YYYY-MM-DD) []:
New account will be created as follows:
---------------------------------------
Login name.......: printemail
UID..............: [ Next available ]
Initial group....: users
Additional groups: [ None ]
Home directory...: /home/printemail
Shell............: /bin/false
Expiry date......: [ Never ]
This is it... if you want to bail out, hit Control-C. Otherwise, press
ENTER to go ahead and make the account.
Creating new account...
Changing the user information for printemail
Enter the new value, or press ENTER for the default
Full Name []:
Room Number []:
Work Phone []:
Home Phone []:
Other []:
Changing password for printemail
Enter the new password (minimum of 5, maximum of 127 characters)
Please use a combination of upper and lower case letters and numbers.
New password:
Bad password: too short.
Warning: weak password (enter it again to use it anyway).
New password:
Re-enter new password:
Password changed.
Account setup complete.

root@monitor:~# usermod -p R@nd0Mp@ssw0rd printemail

root@monitor:~# usermod -L printemail

I disable the account from remote logins for security. Slackware's cron daemon does not
use the users shell anyway.


**Configure Fetchmail**

Use fetchmail to obtain mail from remote locations.

printemail@monitor:~$ cat .fetchmailrc
poll mail.example.org with proto POP3 and options no dns
user 'support' there with password 's3cr3t' is 'printemail' here and wants mda "/usr/bin/procmail -d %T" options nokeep flush

printemail@monitor:~$ chmod 0710 .fetchmailrc


**Script mailx to print email**

Create a mailx command file that:

  a. prints the first email
  b. deletes the first email
  c. quits the program

* note: I tried to do this using mailrc but the program would not respect the quit command
when there were more than 2 emails in the mailbox !*?

#.mailcmd
set cmd=/usr/bin/lpr
set page=yes
set pipe-text/html="lynx -dump -force_html /dev/stdin"
#mailrc would not respect the quit command
folder /var/mail/printemail
pipe 1 /usr/bin/lpr
delete 1
quit


Then write a bash script to run mailx until no new mail exists in the mailbox.

#!/usr/bin/bash
#/usr/local/bin/print_email.sh
#fetch the new mail
/usr/bin/fetchmail > /dev/null
#print all new mail
while ( /usr/bin/mailx -e > /dev/null 2>&1 ); do
  /usr/bin/mailx -B < ~/.mailcmd ;
  sleep 1 ;
done

**Schedule the job**

Finally you would want to cron the job so that it runs every five minutes.

root@nebula:~# crontab -l | grep print_email
# print_email every five minutes
*/5 * * * * /usr/local/bin/print_email.sh 1> /dev/null

---

### Post by Andre81 on 2013-03-07
Hi infotek,

I'm not ubuntu user, but I'ma debian user (newbe)
I've follow your step, but I'm little confusing:

**1- ****[B]Configure Fetchmail**

[/B]this is done in the user printemail, and the configuration of global fetchmail?[B]

2- [/B][B]Script mailx to print email
[/B]I've crated the file .mailcmd in root user folder is this correct?
Who is the owner of print_email.sh?

[B]3- Schedule the job
[/B]Finally your scheduled job is under root.


Thanks for your reply

A.

---


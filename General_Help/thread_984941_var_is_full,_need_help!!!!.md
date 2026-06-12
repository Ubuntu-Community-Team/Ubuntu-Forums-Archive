---
title: "/var is full, need help!!!!"
date: 2008-11-17
forum: General Help
---

### Post by em4g.3ht on 2008-11-17
this is the second time that /var has filled up in a one week period.

I have tried to keep my cool and solve this myself, but I am stumped

here's how my hard drive is partitioned:

sda1 - / - ext3
sda2 - /var - reiserfs
sda3 - swap
sda4 - /home - ext3


also its only a few files that are huge!

here they are:

/var/log/syslog -3.1 gigs
/var/log/messages -2.8 gigs
/var/log/messages.0 - 1.6 gigs
/var/log/kern.log -3.1 gigs


my /var shouldn't be more than 11 gigs should it?

im also showing a constant 20 - 25 % cpu usage but when i look at the active processes there is nothing.. :confused:  perhaps constant disk writing?

any help would be great!


- oh i almost forgot, if it's relevant, I am using Intrepid, on a Lenovo y510 (stock) laptop

---

### Post by scragar on 2008-11-17
I'd run top, see what the most intensive process is.

As for your logs, I've no idea why they are so large, it's clearly not normal, I know scanning to the end of the logs to add new content all the time might be a bit intensive, so that may be the problem.

It might be wise to look through your logs to see what error messages you are getting, or what is repeated to see what's filling up the logs.

---

### Post by geirha on 2008-11-17
Apparently logrotate isn't running on your system. logrotate should be executed by anacron once a day to compress and rotate log files so they don't grow that large.

Does syslog show anacron being run? ```
grep anacron /var/log/syslog
```

---

### Post by reality1011 on 2008-11-17
You should research the logrotate.d directory and increase the frequency of your logs being deleted...  

Here is a good link:
[http://www.watchingthenet.com/how-to-manage-log-file-size-archive-deletion.html](http://www.watchingthenet.com/how-to-manage-log-file-size-archive-deletion.html)

---

### Post by rozilla on 2008-11-17
> **em4g.3ht said:**
> this is the second time that /var has filled up in a one week period.

I have tried to keep my cool and solve this myself, but I am stumped

here's how my hard drive is partitioned:

sda1 - / - ext3
sda2 - /var - reiserfs
sda3 - swap
sda4 - /home - ext3


also its only a few files that are huge!

here they are:

/var/log/syslog -3.1 gigs
/var/log/messages -2.8 gigs
/var/log/messages.0 - 1.6 gigs
/var/log/kern.log -3.1 gigs


my /var shouldn't be more than 11 gigs should it?

im also showing a constant 20 - 25 % cpu usage but when i look at the active processes there is nothing.. :confused:  perhaps constant disk writing?

any help would be great!


- oh i almost forgot, if it's relevant, I am using Intrepid, on a Lenovo y510 (stock) laptop

You have way too much data in those logs. You don't need any logfile to be that big.
What I do is I delete them at the start of each week. Here's a cron job I use for that

```
#!/bin/bash
rm -rf /var/log/*.log.*
rm -rf /var/log/debug.*
rm -rf /var/log/*.err.*
rm -rf /var/log/*.info.*
rm -rf /var/log/*.warn.*
rm -rf /var/log/messages.*
rm -rf /var/log/syslog.*

rm -rf /var/log/apache2/access.log*
rm -rf /var/log/apache2/error.log*
cp logcreate access.log
cp logcreate error.log
chown root:adm access.log
chown root:adm error.log
/etc/init.d/apache2 restart

```

Alternatively, you can also have cron run this script once your logfiles reach a certain size limit. 

I have a separate script for deleting my squid logs, because I still haven't been able to implement logrotate properly for squid logs. These log files can get very large, very quickly. 
So, you need to either keep an eye on them, or let cron to the job for you every week. Or every two weeks, depending on how fast your files grow.

---

### Post by chrisccoulson on 2008-11-17
Any idea what messages are filling up your logs?

---

### Post by em4g.3ht on 2008-11-17
thanks suggestion to use top, it showed my processes not being more than 6% (mostly firefox with a ton of tabs open) total, so I guess there is a bug in the system monitor.

anacron is being run, although logs only show it being run today (no instances of it being run in the past). which is strange so I typed

ls /etc/*cron* and I get this:
```
/etc/anacrontab  /etc/crontab

/etc/cron.d:
anacron

/etc/cron.daily:
0anacron  apt       bsdmainutils  logrotate  mlocate   sysklogd
apport    aptitude  exim4-base    man-db     standard

/etc/cron.hourly:

/etc/cron.monthly:
0anacron  standard

/etc/cron.weekly:
0anacron  apt-xapian-index  man-db  popularity-contest  sysklogd

```

and you can see it's being run every day.

This brings up another question. Is it safe just to delete those over-sized files?

and it seams after anacron being run last night, those log files which were in plain text did get archived to something like this

messages is now 1.6kb   but messages.0 is 2.8 gigs, which is the previous size of the messages file

and my /var is still the same size as it was last night.


Thanks for all the replies btw :)

---

### Post by ibuclaw on 2008-11-17
This is actually a bug in the kernel with your Intel Wireless Card (You are running a Laptop?)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)

There has been a supposed patch for this that fixes this bug.
Though, the Ubuntu Kernel team have still kept this bug marked as "Open/Triaged" until (I presume) further notice.

So you may be safe from now on :)

Just truncate the file and overwrite them.

```

sudo rm /var/log/messages.0
tail /var/log/messages | sudo tee /var/log/messages.new
tail /var/log/syslog | sudo tee /var/log/syslog.new
tail /var/log/kern.log | sudo tee /var/log/kern.log.new
sudo mv /var/log/messages.new /var/log/messages
sudo mv /var/log/syslog.new /var/log/syslog
sudo mv /var/log/kern.log.new /var/log/kern.log

```

Regards
Iain

---

### Post by geirha on 2008-11-17
It's safe to delete them since no applications uses the contents of those files. The logfiles are for users and developers to interpret what applications are doing. Typically to figure out why a certain application doesn't work as expected. 

As for why anacron hasn't been running regularly. Anacron is run each morning and during boot, and runs the scripts in /etc/cron.{daily,weekly,monthly} if it is more than 1 day/week/month since last it was run. Anacron is turned off when a laptop is running on batteries though, so you might have been running on batteries all the times it was supposed to run.

---

### Post by em4g.3ht on 2008-11-17
thanks for are your help everybody, my /var partition is now down to a more manageable 3 gig :)

also I am using a laptop, with an intel wireless card, so I am assuming this was a bug because I have never had a problem with run-away /var size on any of my desktops.

---


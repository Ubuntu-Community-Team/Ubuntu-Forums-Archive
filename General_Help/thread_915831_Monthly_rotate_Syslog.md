---
title: "Monthly rotate Syslog"
date: 2008-09-10
forum: General Help
---

### Post by ngmachado on 2008-09-10
Hi,

My Ubuntu 8.04 LTS is rotating syslog file every day (and keeping logs for 7 days), the default option. 

The other system logs (auth.log, mail.log, messages) are rotating every week, and files are kept for 4 weeks.

I came to this conclusion by checking the files:

/etc/syslog.conf
/etc/cron.daily/sysklogd
/etc/cron.weekly/sysklogd
/etc/crontab

Since my server is not a busy one, disk space is not a problem and I want to have a better overview of my logs (without having to untar everytime), I would prefer to have a monthly rotation of ALL my logs, and keep logs for the past 3 months.

The problem is, I don't know what to change in the files I mentioned to make it happen. :( If you can help, I'll be very glad.

---

### Post by iaculallad on 2008-09-10
On your terminal:

```
sudo vi /etc/logrotate.conf
```

Change "rotate 4" to "rotate 2" and then change "weekly" to "monthly".

---

### Post by ngmachado on 2008-09-10
Hi iaculallad,

I really appreciated your help but I've to remember you that in Ubuntu the rotation of system logs are not handled by logrotate but by savelog. :(

> I have split this article in two parts based on the way how the log rotation is handled:

**system log files**: most of the system log files are rotated by syslog itself and not using logrotate. You will see here what are these log files, and how they are rotated.

**application log files**: logrotate is the default choice to rotate all the other log files. It can rotate the logs based on various parameters: daily, weekly, monthly, based on the size of the log, it can compress the logs to save space, etc.

in: [http://www.ducea.com/2006/06/06/rotating-linux-log-files/](http://www.ducea.com/2006/06/06/rotating-linux-log-files/)

---

### Post by iaculallad on 2008-09-10
Yes, that should not be logrotate. Try editing this file to meet your needs:

```
/etc/cron.weekly/sysklogd
```

Or try moving it in the cron.weekly folder if it could be possible.

---

### Post by ngmachado on 2008-09-10
After reading a bit about my problem, it seems that it's *not* possible to make the system logs rotate in a monthly basis.

[https://bugs.launchpad.net/ubuntu/+source/sysklogd/+bug/255226](https://bugs.launchpad.net/ubuntu/+source/sysklogd/+bug/255226)

:(

---

### Post by ngmachado on 2008-09-15
Hi,

After reading a lot more about this subject, one should install Syslog-ng to have control over the rotation period of system logs.

Among several other features (like remote/database logging), Syslog-ng relies on the famous logrotate tool to rotate logs.

Check the following links if you want more help:

[http://sial.org/howto/logging/syslog-ng/](http://sial.org/howto/logging/syslog-ng/)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch05_:_Troubleshooting_Linux_with_syslog](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch05_:_Troubleshooting_Linux_with_syslog)

Cheers.

---


---
title: "How to change the syslog rotation schedule?"
date: 2008-10-31
forum: General Help
---

### Post by zuehls on 2008-10-31
I have some questions regarding rotating the syslog.  I am using the default syslog service that came with Ubuntu 8.10

1.  Can you change the schedule for rotating the syslog?
2.  Can you change the schedule so the syslog is rotated weekly instead of daily?

thx

---

### Post by dcstar on 2008-10-31
> **zuehls said:**
> I have some questions regarding rotating the syslog.  I am using the default syslog service that came with Ubuntu 8.10

1.  Can you change the schedule for rotating the syslog?
2.  Can you change the schedule so the syslog is rotated weekly instead of daily?

thx

man logrotate

---

### Post by zuehls on 2008-11-01
My understanding is that logrotate does not rotate logs for syslog.  I understand it rotates logs for applications but not the system.  Is this new in 8.10?

---

### Post by latimerio on 2012-04-30
Ubunutu uses 2 log rotation mechanisms.

System log files which are configured via ***/etc/syslog.conf*** are rotated through ***/etc/cron.*/sysklogd*** which in turn uses the perl script ***/usr/sbin/syslogd-listfiles*** to get the list of files which need to be rotated.
The other tool is ***logrotate ***which is configured through ***/etc/logrotate.conf*** and scripts in */etc/logrotate.d*

The advantage of the sysklogd mechanism is that new syslog files added to syslog.conf are automatically rotated without writing an extra logrotate script.

syslogd-listfiles is a bit complex and it rotates some logfiles on a daily bases which is not always useful on an inactive system.
So on my system I set "$everything=0 ;" in the lower section of the perl script to disable the daily rotation of *.* syslog entries thus changing the default to rotate purely based on log file size.

---


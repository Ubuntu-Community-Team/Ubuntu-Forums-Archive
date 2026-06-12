---
title: "Server Reboots Every Few Days..."
date: 2013-01-27
forum: Hardware
---

### Post by Kirk Schnable on 2013-01-27
I am troubleshooting what I suspect is a hardware problem (hence why I've posted in the Hardware section).  I have a server that is several years old, and over the past few months I have noticed that it is periodically rebooting on its own.

It is just a home server for my personal use, and I'm not home that much recently due to college and work anyway, but it's becoming a problem because instead of every few weeks, it's started to reboot every few days.  It seems to occur at odd times of day when the server is sitting idle.

I decided to dive into the syslogs and see if I could find out why.

I've pinpointed one of the time periods when a random reboot occurred.  January 26th, 2013 at 4:59am.  I do have overnight jobs scheduled, but they're just rsync backups, and I would think they would have been finished by then. 

```
Jan 26 04:17:01 Scimitar CRON[23167]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 26 04:59:12 Scimitar kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan 26 04:59:12 Scimitar rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1384" x-info="http://www.rsyslog.com"] start
Jan 26 04:59:12 Scimitar rsyslogd: rsyslogd's groupid changed to 103
Jan 26 04:59:12 Scimitar rsyslogd: rsyslogd's userid changed to 101
Jan 26 04:59:12 Scimitar rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jan 26 04:59:12 Scimitar kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 26 04:59:12 Scimitar kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 26 04:59:12 Scimitar kernel: [    0.000000] Linux version 3.2.0-36-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 (Ubuntu 3.2.0-36.57-generic 3.2.35)
```

It looks like there is no syslog information that is relevant whatsoever... it's as if the plug was just pulled.

It is not a problem with the power source, as the server is on a UPS, and shares that UPS with a wireless access point that has been operational for 33 days.

What sort of hardware issue should I be looking for here?

This specific type of problem makes me suspicious of the power supply.  I would assume if I had a motherboard, CPU, or RAM issue that I would most likely be seeing a kernel panic or some other type of error before the server offs itself?

I would appreciate any input you folks have.

Thanks!
Kirk

---

### Post by Kirk Schnable on 2013-01-27
I went ahead and ordered a new power supply for it.  It had a rather specific power supply before as it has 8 SATA hard drives.

I paid over $100 for the power supply 4 or 5 years ago.... it has since survived a direct lightning strike that blew out other appliances on the same circuit.

I would be very understanding if it had decided to start failing now, 2 years after being hit by lightning as it's turning 5 years old.

I looked it up on NewEgg, and felt fortunate to see that they're still selling it, and for about what I paid for it years ago.  Also had a $30 promo code and $20 mail in rebate, so I felt like it was worth it.  If it doesn't fix the problem, I'll use it for something else.  :)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139012](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139012)

I'll let you know how it goes once the new unit is installed.

Kirk

---


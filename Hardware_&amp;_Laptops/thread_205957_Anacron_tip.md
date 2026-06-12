---
title: "Anacron tip"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by FuturePast on 2006-06-29
Anacron is responsible for making sure that daily, weekly and monthly maintenance scripts are run when a machine does not tend to be on 24hrs a day.

In Ubuntu it does this by checking at boot time if the scripts have not yet been run that day, or by doing the same check every morning at 7.30am.

If you are anything like me then your laptop is certainly not on at 7.30am and is rarely booted because the laptop is kept in suspend overnight and for parts of the day.  This means that the daily maintenance scripts may rarely be run.

To resolve this I placed the following short script in [FONT="Courier New"]/etc/cron.hourly[/FONT]

> #!/bin/sh

test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null

This means anacron checks each hour (default is at 17mins past the hour) whether it needs to run the daily scripts.

---


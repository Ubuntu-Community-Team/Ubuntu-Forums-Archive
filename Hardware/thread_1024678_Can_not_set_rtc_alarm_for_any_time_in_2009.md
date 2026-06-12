---
title: "Can not set rtc alarm for any time in 2009"
date: 2008-12-29
forum: Hardware
---

### Post by glennric on 2008-12-29
I usually set the rtc alarm to wake my computer every Sunday morning, and then cron jobs run to back up my system.  I created an init script to set the alarm at boot up, and this script is also run after the backups are done to set the alarm for the next weeks time.

That ran this week and tried to set the alarm for next week.  Now, if I try to view the alarm time with "cat /proc/driver/rtc" it completely locks up the computer for a minute or so, and then it finally responds and the alarm date is "****-01-04", not "2009-01-04" as expected.  Things work as they should if I try to set the alarm for a future time in 2008.

Has anyone else noticed this?  What is going on?

---


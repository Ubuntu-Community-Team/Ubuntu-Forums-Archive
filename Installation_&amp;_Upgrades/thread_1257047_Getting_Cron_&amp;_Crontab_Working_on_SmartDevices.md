---
title: "Getting Cron &amp; Crontab Working on SmartDevices Q5 and Q7"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by celtica96 on 2009-09-03
I'm an Ubuntu/Linux newbie so please excuse any ignorance reflected in the following problem statement.

I would like to use cron to run an hourly script on my SmartQ 5 and 7. (These are handheld Mobile Internet Devices running Ubuntu.)

According to the hardinfo app, the kernel is Linux 2.6.24.7 (armv6l), the C Library is GNU C v. 2.7 (stable), and the distribution is Handhelds 8.04.

The problem is that the OEM, SmartDevices, does not seem to have fully installed cron and crontab.

The folder /etc/ contains the expected subfolders for cron.d, cron.daily, cron.monthly, and cron.weekly.

The system-wide crontab file should be found in /etc/crontab but no such file exists.

Also, there should be a user-specific crontab found in /usr/bin/crontab but that does not exist either.

I tried using gnome-schedule to create a crontab but it failed because it couldn't find either the system crontab or the user crontab.

Does anyone have a suggestion other than accepting that I'm in over my head?

Thanks in advance.

---

### Post by celtica96 on 2009-09-04
Someone on mobileread.com pointed out my error.

I originally tried to install cron & crontab using "sudo apt-get install crontab" when it should have been "sudo apt-get install cron". 

The former gives the error of "Couldn't find package crontab" and I was stumped because I didn't think to try the latter. I thought the setup on the Q5/Q7 was to blame.

When I tried the latter, cron & crontab installed fine and everything worked.

Hurray! Problem solved. :)

---


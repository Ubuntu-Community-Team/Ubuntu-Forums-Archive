---
title: "optimization for laptops - syslog/cron"
date: 2009-02-03
forum: Hardware
---

### Post by Dummy00001 on 2009-02-03
Hi All!

I'm again trying to optimize my ex-ubuntu 8.04 (now running with xubuntu) to be a good laptop system. 

N.B. This is quite old Apple PowerBook 12". Stats: under Mac OS X 10.3 runs from batter for about 3.5 hours; Linux (Ubuntu/Xubuntu) - measly 1.5 hours.

One of the major usual complains is that under Linux harddrive is always spinning.

With "pidstat -d 10" gnome-network-manager was identified (writes every 90 seconds state of battery to disk) and removed. (The ridiculous behavior prompted me even to submit bug to launchpad.)

Now I'm trying to remove next biggest offender: syslog and cron. The problem is that cron always has something to do. But that's in itself not a problem: cron sends its command to syslog and syslog obediently sends it to /var/log/syslog. And this happens sometimes as often as every 5 minutes.

The question I have now: how to remove cron messages from syslog? Apparently /etc/syslog.conf has catch all entry '*.*' for /var/log/syslog. And even if I add entry to send 'cron.=notice' (normal messages from cron (as per man anacron)) to /dev/null, catch-all rule '*.*' still sends copy to /var/log/syslog.

Is it possible to somehow prevent cron from sending non-errors to syslog? Is there any way to tell syslog to drop message after some rule already matched?

---

### Post by motin on 2009-04-25
Cron-issue solution here: [http://ubuntuforums.org/showthread.php?p=5380616](http://ubuntuforums.org/showthread.php?p=5380616)

---


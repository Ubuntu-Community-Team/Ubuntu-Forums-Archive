---
title: "[SOLVED] NTP not working automatically"
date: 2008-08-12
forum: General Help
---

### Post by usererror on 2008-08-12
I am having an issue with NTP.  It simply does not update the clock!  

If I use 'sudo ntpdate 192.168.12.254' then it updates the clock.  192.168.12.254 is my NTP server.  

I cannot find anything log wise to indicate why the NTP service is not working, and it is running.  

ntpdate will not work unless I stop the NTP service.

There is a script in one of the cron jobs that is called NTP, but it does not appear to run, either.

Any help is appreciated!


**EDIT**

It seems to be fixed?  Not sure why, but in /etc/ntp.conf I have logged turned on to /var/log/ntpstats/ which it was not doing...i appended 'ntplog' to the end of /var/log/ntpstats/ntplog and now it is logging.  So why did it need a file name added??  it then appends 'peerstats' / 'loopstats' to the file name I added...odd.

---


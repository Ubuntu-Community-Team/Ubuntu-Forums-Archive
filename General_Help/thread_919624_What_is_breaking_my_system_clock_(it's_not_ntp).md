---
title: "What is breaking my system clock (it's not ntp)"
date: 2008-09-14
forum: General Help
---

### Post by chackoc on 2008-09-14
Basic problem is that something is changing my system time every 10 seconds.  

I've got my hardware clock set correctly based on hwclock.

To monitor what's going on I start this running in one terminal

watch --interval=0.5 'date ; ps -ef | grep ntp | grep -v grep'


I then set the system time to the correct time using the following command in another terminal.

hwclock -s

The time shown by the watch output will be correct for a few seconds and then it will get changed to the incorrect time.  

Does anyone know what could be doing this?  I've stopped ntp via /etc/init.d/ntp stop

ps -ef | grep -i ntp also shows nothing running.

I've even gone so far as to rename /usr/sbin/ntpdate to see if something was calling that, but the time still gets changed even when /usr/sbin/ntpdate doesn't exist. 

I was hoping the ps in the watch command would identify ntp as the culprit if that was it, but the watch command doesn't show anything when the time get's switch.  One iteration the time is fine the next it's been changed.

Does anyone know what the problem might be or what I can do to track it down?  Searching google and these forums hasn't turned up much.  

Also, I don't know if it matters but this is an fluxbuntu installation running in VirtualBox.  The fact that the hwclock is fine in all this leads me to believe that isn't an issue.

---


---
title: "Crash / Freeze (Logs give nothing...)"
date: 2008-08-14
forum: General Help
---

### Post by blackbinary on 2008-08-14
This is on a fresh install of 64bit 8.04 ubuntu.
I had ubuntu installed previous, and when these crashes started to happen, i decided to try to reinstall ubuntu. 

Now that it continues to happen, I'm looking for some help.

I've looked at the logs in var/logs/messages and var/logs/syslog. both give nothing relevant at the time of the crash, for example syslog will give --- MARK--- and the next entry is -Ubuntu restarted. No explanation :(

The only thing it may be (from a few times in the logs..) is
  	
Aug 14 16:20:15 blackbinary-desktop kernel: [   88.834980] eth0: no IPv6 routers present
Aug 14 16:20:24 blackbinary-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 14 16:20:24 blackbinary-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

A few times in the log i get that <WARN> which is followed closely by the time it crashes. eth0: no IPv6 routers present also seems to pop up a lot.

This is a desktop, and it is wired, so I don't need it checking for wireless networks.

Any suggestions on what to do? (Also i am a bit of a newbie, so try not to be vague)

----> EDIT: That may not be it. I disabled looking for wireless,  thinking that would solve the problem. As you can see it was 18 minutes between the disable and the mark, which was when it restarted. It didnt spit out any useful info. Still if someone has an idea let me know please. 
Aug 14 19:31:55 blackbinary-desktop NetworkManager: <info>  User request to disable wireless. 
Aug 14 19:31:55 blackbinary-desktop NetworkManager: <info>  Deactivating device wlan0. 
Aug 14 19:49:31 blackbinary-desktop -- MARK --
Aug 14 16:05:41 blackbinary-desktop syslogd 1.5.0#1ubuntu1: restart.

---


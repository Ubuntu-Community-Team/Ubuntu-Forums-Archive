---
title: "upgrade to 9.0.4 to 9.1.0 failed"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by vkumar23 on 2009-11-07
hi all

I just tried upgrading to 9.10 from 9.04 using the update manager. During updation, it threw an error saying, upgrading failed. 

I checked to logs in /var/log/dist-upgrade/apt.log

2009-11-07 21:51:12,910 DEBUG check if patch '_usr_sbin_install-docs.268d21f1f1ed5f7a19fffef645ac4d52' needs to be applied
2009-11-07 21:51:12,910 DEBUG check if patch '_usr_sbin_install-docs.3533d3b8e8f08f78c95550a7edcbe316' needs to be applied
2009-11-07 21:51:12,911 DEBUG killing update-notifier
2009-11-07 21:51:12,925 DEBUG killing kblueplugd kbluetooth4
2009-11-07 21:51:12,940 DEBUG killing gnome-screensaver
2009-11-07 21:51:12,954 INFO cache.commit()
2009-11-07 21:51:13,906 ERROR SystemError from cache.commit(): installArchives() failed
2009-11-07 21:51:19,225 DEBUG enabling apt cron job
2009-11-07 21:51:19,225 DEBUG Running PostInstallScript: './xorg_fix_proprietary.py'
2009-11-07 21:51:23,470 DEBUG enabling apt cron job

the error says Install Archives failed

Can you give me some pointers on how i can check what the problem is . I doubt its one of my old installed programs which cannot be upgraded causing the problem

all help appreciated

thanks
vinod

---


---
title: "Synaptic broken?"
date: 2008-08-30
forum: General Help
---

### Post by MeanStreak on 2008-08-30
Hi,

I'm getting the following message when I open Synaptic. Could someone please advise?

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```

---

### Post by hansdown on 2008-08-30
Hi MeanStreak.

You need to go to applications>terminal, and run dpkg --configure -a

You can copy and paste if you like. Hit enter.

Hope this helps.

---

### Post by perlluver on 2008-08-30
actually you want to run in a terminal, ```
sudo dpkg --configure -a
```

---

### Post by MeanStreak on 2008-09-01
Thanks. I ran the following in a terminal:
```
sudo dpkg --configure -a
```

This was the result:

```
charles@charles-desktop:~$ sudo dpkg --configure -a
[sudo] password for charles: 
dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kdebase-data (>> 4:3.5.10); however:
  Package kdebase-data is not installed.
 kcontrol depends on kdebase-data (<< 4:3.5.11); however:
  Package kdebase-data is not installed.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
Setting up kfind (4:3.5.10-0ubuntu1~hardy1) ...

dpkg: dependency problems prevent configuration of kicker:
 kicker depends on kdebase-data (>> 4:3.5.10); however:
  Package kdebase-data is not installed.
 kicker depends on kdebase-data (<< 4:3.5.11); however:
  Package kdebase-data is not installed.
dpkg: error processing kicker (--configure):
 dependency problems - leaving unconfigured
dpkg: failed to write status record about `exim4-daemon-light' to `/var/lib/dpkg/status': No space left on device
```

---

### Post by MeanStreak on 2008-09-01
Seems my root directory was full so Synaptic had no where to install any new packages. 

How had my root directory become so full after I'd recently re-partitioned it? The answer lies with a basic back-up program called Simple Backup. I configured this to automatically back up my Home directory every week to an external drive called MyBook. Only, if the MyBook HDD wasn't attached, Simple Backup created its own directory in /Media and proceeded to save over 20GB worth of compressed data there - every week - until the root directory was full. With no warning. Nor did Ubuntu ever warn the root was becoming full. Talk about an app that is not ready for primetime. Even the most trivial program should prompt when its configured destination drive is not present. 

While the Ubuntu community continues to provide excellent support, this is one user who will be moving to Mac. I don't have time to troubleshoot these errors every evening.

---


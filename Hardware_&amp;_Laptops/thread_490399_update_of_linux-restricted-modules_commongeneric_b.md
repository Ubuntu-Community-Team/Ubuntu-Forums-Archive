---
title: "update of linux-restricted-modules common/generic breaks external monitor on nvidia"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by =JeffH on 2007-07-02
The recent update (Fri 2007-06-29 US pacific time) to..

2007-06-29 06:54:06 upgrade linux-restricted-modules-common 2.6.17.7-11.2 2.6.17.8-11.2

2007-06-29 06:54:07 upgrade linux-restricted-modules-2.6.17-11-generic 2.6.17.7-11.2 2.6.17.8-11.2

..apparently has broken my xorg multiple-monitor setup on my Dell D820 running Edgy (6.10)

I was notified of the available update when I booted up in the morning, installed it, and worked all day (running the nvidia  100.14 11 driver and using both the builtin LCD and an external monitor, as usual), shutdown, and when I booted up Saturday morning, the xorg server crashed on initialization. 

I have multiple /etc/X11/xorg.conf.* files lying around, and so experimented with both multi-screen setup using the "nv" (open source nvidia driver) and "nvidia" (proprietary nvidia driver), and with both, the X server crashes. [i just symlink /etc/X11/xorg.conf to the "real" xorg config file I wish to try and restart the X server]

I can get the system to work by using an xorg.conf that utilizes only the builtin LCD monitor and the "nv" driver. I haven't tried this with the "nvidia" driver.

Anyway, it seems to me that something in the upgrade of the above two linux-restricted-modules-* is breaking things in that I hadn't changed anything else in the system config except the above two listed upgrades (before the failure began).

Below are the applicable log files, created by nvidia-bug-report.sh (a cool tool that includes a host of information  including the xorg.conf file, the nvidia driver initialization log, etc). The first log is a diff between the other two logs, which are for the nvidia driver failure, and the nv driver failture. The diff log is 400 cols wide. 

Questions: 

0. obviously, anyone know what changed in the above packages that woulda done this? 

1. How does one figure out exactly what are the changed/new modules in the above listed package upgrades?

2. How might I back out the upgrades so I can get my multiple-monitor setup working again?

[this thread is related to these nvidia forums (nvnews.net) threads..
[http://www.nvnews.net/vbulletin/showthread.php?t=94205]("http://www.nvnews.net/vbulletin/showthread.php?t=94205")
[http://www.nvnews.net/vbulletin/showthread.php?t=94187]("http://www.nvnews.net/vbulletin/showthread.php?t=94187")
]

Please let me know if there's any other info I can supply to help figure this out.

thanks!

=JeffH

---

### Post by =JeffH on 2007-07-02
As I note in my followup over in the thread on nvnews.net (pointer to thread in post above), re-installing the nvidia driver-- using the same version I had previously installed -- fixed the issue. 

=JeffH

---


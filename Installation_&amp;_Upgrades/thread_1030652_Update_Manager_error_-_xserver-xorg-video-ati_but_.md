---
title: "Update Manager error? - xserver-xorg-video-ati but I have Nvidia graphics card"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Frankenpunk on 2009-01-04
Update manager wants to download xserver-xorg-video-ati and xserver-xorg-video-radeon, but I have an Nvidia graphics card. I have found someone else with the same confusion, but I cannot determine why those updates are queued for download/installation.

Should I remove them? Install them?

Please let me know if I should be asking this somewhere else.

---

### Post by staticsage on 2009-01-04
This just showed up in my update list as well. They're already installed on my system (these are just updates) so I assume the updates are correct. Has anyone else seen this before?

```
$ apt-cache policy xserver-xorg-video-ati
xserver-xorg-video-ati:
  Installed: 1:6.9.0+git20081003.f9826a56-0ubuntu2
  Candidate: 1:6.9.0+git20081003.f9826a56-0ubuntu2.1

```

Edit: I installed the updates and rebooted and nothing broke.

---

### Post by Frankenpunk on 2009-01-08
Apparently some ati drivers are installed by default when you install ubuntu. Update manager is just detecting that there are newer versions of those (even though you're not using them). I just uninstalled my ati-specific drivers and everything seems to be running fine; and perhaps I'll stop being pestered by the updates that don't apply to my system.

---


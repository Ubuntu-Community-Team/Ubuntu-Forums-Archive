---
title: "Hotplug-Blacklist MP3 Player ?"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by cleersf on 2007-05-02
I am interested in disabling my MP3 player from automatically loading when I plug it into my computer. I am using VMware with XP and need for this device to not mount so that it can mount in XP...so they say. I have been reading some articles and posts that talk about a blacklist file for hotplug that I can add the device to, but haven't been able to figure this one out. Thank you.

---

### Post by 5-HT on 2007-05-02
Are you using Gnome? If so, easiest way would be to head over to System > Preferences > Removable drives and Media, and deselect 'mount removable drives/media when hot-plugged/inserted' to your liking. 
You can always mount the device manually in Ubuntu when needed afterwards.

---

### Post by cleersf on 2007-05-02
Yes, I'm using Gnome, Feisty...  the thing is VMware says that I need to have VMware-guest OS in focus when I plug my device in, while having it set not to mount automatically in Ubuntu. I would like to disable it mounting in Ubuntu when I initially plug it in.

---

### Post by cleersf on 2007-05-08
I found what I needed to do...Just for reference for new VMware users who want to use USB mp3 player in WinXP, you must turn off the ability to mount removeable media in: **System:Preferences:Removable Drives and Media**

I had no clue, so maybe this will help a newbie too.

---


---
title: "Backup and re-install question"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by tandrecht on 2009-04-29
I'm going to need to re-install Ubuntu on my desktop as my old mobo is dead and will likely be switching from intel to amd hardware, so I want to grab all of my stuff before i wipe the disk and reformat.  Most of it I've found, but I have a rather extensive whitelist in IPBlock that I want to save and restore when the system is back.  Can anyone tell me how I can save it and restore it back later (hopefully just a copy out and paste back, but I'm ready to do whatever I can to get it).  Thanks.

---

### Post by empthollow on 2009-04-30
check out this thread
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by uljanow on 2009-04-30
The whitelist feature of IPblock stores the permanent ranges in **/var/cache/iplist/allow-perm.p2p**. Saving the file and copying it back after installing iplist should work.

---

### Post by tandrecht on 2009-05-02
Didn't have what I was looking for.  Don't want a full system backup, just certain files as I doubt I'll be able to use an intel image on an amd mobo.  Thanks though.

---

### Post by tandrecht on 2009-05-02
> **uljanow said:**
> The whitelist feature of IPblock stores the permanent ranges in **/var/cache/iplist/allow-perm.p2p**. Saving the file and copying it back after installing iplist should work.
Great, this is exactly what I need.  Thanks.

---


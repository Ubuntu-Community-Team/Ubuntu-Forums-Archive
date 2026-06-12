---
title: "Files/Folders to make reinstall/troubleshooting easier?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by xarte on 2008-12-17
I was flicking through APC magazine in the newsagent and it mentioned some folders to copy onto a USB stick to make re-installing and troubleshooting easier.  Anyone suggest what these are? 

(I didn't want to buy the whole mag for a one-paragraph tip. Plus I already bought two linux mags this week.)

I was just wondering about this as with Warcraft updates/installs, Vista updates and several linux reinstallations I might finally exceed my ISP download limit.

Can I save updates and packages to disk or USB drive to save downloading them yet again? (Another reason to use CLI rather than the autopilots on the desktop, I guess)

Tanks!

---

### Post by jpkotta on 2008-12-18
Recently installed packages are stored in /var/cache/apt/archives/.  If you reinstall frequently, you should know about a separate /home partition.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by xarte on 2008-12-19
thanks. that's really useful.

I'll have to make that separate home partition, that sounds like a good idea. I'm pretty happy with this install, but its only a matter of time before I decide to change it.

That means I'll need to do a clean install, doesn't it. (Sheesh I hate having to ask something that should be so basic).

Might be a good time to give 8.10 a quick spin ...

---


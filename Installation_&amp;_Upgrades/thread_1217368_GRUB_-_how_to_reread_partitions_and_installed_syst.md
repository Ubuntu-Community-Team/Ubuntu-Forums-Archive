---
title: "GRUB - how to reread partitions and installed systems? [grub, reinstall, recheck]"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Abdus on 2009-07-19
[COLOR="DarkOrange"][question, problem][/COLOR]
How can I make GRUB reread (recheck? update?) all the disks in order to compose a brand new list of installed operating systems and boot options, and then write it to boot sector of my first drive?

[COLOR="DarkOrange"][story, i.e. more details][/COLOR]
I removed some previous OS's, then formatted whole disks, partitioned them anew and installed new systems on those new partitions. Every new OS install did remove GRUB boot settings from boot sector in hd0, but this was not a problem, as I just used Ubuntu 9.04 Jaunty installation disk to reinstall GRUB. To my indignation GRUB proved to be lazy and just reinstalled its previous configuration, allowing me to boot nonexistant systems on nonexistant partitions.

I'm an Ubuntu newbie and also a slacking administrator who prefers to use his system rather than to configure it endlessly. Thus I'd rather use a simple command line command to achieve my task and forget about my issue than spend an hour editing grub config files (which would likely lead to serious damage). If a safe, lightweight and simple Gnome GUI exists, it would be also very welcome. But as far as I know when it comes to GRUB things quit being simple (which I find quite amusing, as this application is already years old and using it should be easy as a few clicks).

[COLOR="DarkOrange"][disclaimers and configuration][/COLOR]
I did numerous forum searches. Most of threads I found coped with GRUB restoration (which is not the issue here) or present complicated/tedious solutions, written in times of Jaunty long gone ancestors. 

I use Ubuntu 9.04 Jaunty Jackalope for AMD64, Alternative installation (command line, then the rest).

Thanks for any tips.

---

### Post by Abdus on 2009-07-20
Bump. Still not solved. :)

---


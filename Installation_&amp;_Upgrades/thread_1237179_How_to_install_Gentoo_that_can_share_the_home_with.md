---
title: "How to install Gentoo that can share the /home with Ubuntu"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by loading99 on 2009-08-11
Preparing to install Gentoo in my computer&#65292;but I want Ubuntu & Gentoo use the same /home directory&#65292;it may be better that /swap could be shared to.

how can I do this when creating the partitions?:confused:

---

### Post by tommcd on 2009-08-11
I have never used Gentoo, but when you partition Gentoo (or any distro), you can choose your existing home partition as the mount point for home in Gentoo. 
Gentoo's installer should automatically detect and use your swap partition also.
 
I would recommend that you choose a different user name in Gentoo than you use in Ubuntu. This is to avoid having any potential conflicts between all the hidden config files and directories that are stored in home.
I like to use a /data partition to store my data between distros. This way each distro's home partition is contained within the root partition of each distro, so there is no potential for these conflicts.

And welcome to the Ubuntu forums!

---

### Post by night_fox on 2009-09-23
Hi, I just set up ubuntu to share /home partition with gentoo, and the first thing gentoo did was wreck the config file for the fonts, rendering fonts invisible for a user on ubuntu. I havent thought of a fix yet, but looking ahead, if you want to restore the fonts, look in gconf-editor under /desktop/gnome/font_rendering and restore to:

antialiasing: rgba
hinting: slight

had me confused for weeks

---

### Post by tommcd on 2009-09-24
> **night_fox said:**
> Hi, I just set up ubuntu to share /home partition with gentoo, and the first thing gentoo did was wreck the config file for the fonts...
This is why I recommended to the OP to use a different username in Gentoo than the one he uses in Ubuntu. With a different username the config files should be kept separate so as not to conflict with each other. This is also why I use a /data directory to store my stuff.

---


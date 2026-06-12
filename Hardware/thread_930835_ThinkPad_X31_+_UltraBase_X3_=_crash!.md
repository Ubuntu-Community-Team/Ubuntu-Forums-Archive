---
title: "ThinkPad X31 + UltraBase X3 = crash!"
date: 2008-09-26
forum: Hardware
---

### Post by Gary13579 on 2008-09-26
Recently got an X31 off eBay, for fairly cheap. So far I love it (and am posting this on it).

Installed Ubuntu of course, but whenever I try and undock the UltraBase X3 ([http://www.thinkwiki.org/wiki/UltraBase_X3](http://www.thinkwiki.org/wiki/UltraBase_X3) ), the notebook locks up and requires a restart.

Using kernel version 2.6.24-19, the latest stable release + all updates.

Issuing "sudo echo 1 > /sys/devices/platform/dock.0/undock" will also cause it to crash immediately, without even removing the dock.

(posting under all variants since it shouldn't be specified to a certain distro, correct?)

---


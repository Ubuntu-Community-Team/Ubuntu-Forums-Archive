---
title: "ASRock N68-GS4/USB3 No Ethernet and System Can't close down"
date: 2015-11-24
forum: Hardware
---

### Post by mike16 on 2015-11-24
Just purchased a new PC with the above motherboard - ASRock N68-GS4/USB3.
  Windows 10 works well on it and I've loaded UBUNTU 14.04 as well,  boots up ok into either OS.
  However, with UBUNTU I get 2 problems:
  
[LIST]
[*]System cant see any Ethernet connection ( I haven;t tried WiFi as the house isn't fitted with it.
[*]System hangs on shut down.
[/LIST]
  I found this older thread:
  [https://bbs.archlinux.org/viewtopic.php?id=200749](https://bbs.archlinux.org/viewtopic.php?id=200749)
  and tried to implement the solutions listed at the (2015-08-06  18:58:31) entry.  But that fails because my system doesn't have a  "mkinitcpio.conf"  or even a "mkinitcpio.conf".
  So I followed his link to:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297)
  His solution "1)" works as an emergency measure but only works  once-only and a lot of the graphics drivers are not running optimally.
  He says his "2)" no longer works, so I tried his "replacement"  work-around, but that failed because my system doesn’t have a file at  "/etc/init/module-init-tools.conf"
  I'm hoping taht there is a simple work around for this issue in UBUNTU 14.04 / its' linux kernel .
  Can someone help please?

---


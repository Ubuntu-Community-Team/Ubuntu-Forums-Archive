---
title: "slow usb record and no async option available"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by mvfpoa on 2007-05-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104241](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104241) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Reading the posts on the ubuntuforums, lot of users are complaining about the slow performance of writing on usb devices. They think it is related to the sync mount option.
    I tried to remount my pen drive with async option, but it doesn't makes any difference (doesn't even show in mtab). In the mount man page, there is a paragraph explaining that sync just work on ext filesystems.
    Now I question, why are the record operation so slow on my pen drive on fesity (it was not this slow on dapper). It's not caused by the device, it works where else.

Important: Consider that it is slower than in Dapper.

Greetings!

PS.: I found a file (/etc/hal/fdi/policy/preferences.fdi) where it tries to advice gnome-volume-manager not to mount removable media bigger than 1Gb with sync option. My pen drive is 2Gb.

---


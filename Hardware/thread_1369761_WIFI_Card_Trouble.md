---
title: "WIFI Card Trouble"
date: 2010-01-01
forum: Hardware
---

### Post by jbergsing on 2010-01-01
I have been trying to get my wifi card to work since installing ubuntu with no success. I found a link somewhere in the documentation that had me blacklist the b43 stuff. One thing I noticed was before I did that, the wifi card was on. Now it doesn't turn on at all. And I can't figure out how to remove it from this blacklist. 

Can someone help this Ubuntu newb? Everything else seems to work great but I's really like to break this ethernet cable (chain)!

Thanks, John

---

### Post by IcarusR on 2010-01-02
Blacklisting a module usually involves adding it to /etc/modprobe.d/blacklist
To 'unblacklist' run this in a terminal
> sudo gedit /etc/modprobe.d/blacklist

remove the line that references the module to be unblacklisted, then save file.
When you reboot the module in question should then be loaded.

If you tell us which version of Ubuntu you are running & post output of the following command someone may be able to help get your wireless working.

> lspci

Also post link to instructions you tried to follow.

---


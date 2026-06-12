---
title: "HP DV6 and Ubuntu 11.04, Slow Wireless"
date: 2011-05-21
forum: Hardware
---

### Post by tackyjan on 2011-05-21
I don't want to cross post but I also wanted to give my post a bit better chance to be seen. I am basically have issues with my DV6-3130us running Ubuntu 11.04. The wireless connection is terribly slow! (More than 2 hours for 500Mb file! :( )

If you don't mind can you please see my thread (link below) and respond? ):P

[http://ubuntuforums.org/showthread.php?t=1764604](http://ubuntuforums.org/showthread.php?t=1764604)

---

### Post by sero on 2011-06-01
I find this to help for my DV6 3139TX

"open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta. 
Now, reboot."

This assumes you have RT2XXX wireless card. If it works it also fixes shutdown/reboot issues.

Original post by rtomakov is here: [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)

---


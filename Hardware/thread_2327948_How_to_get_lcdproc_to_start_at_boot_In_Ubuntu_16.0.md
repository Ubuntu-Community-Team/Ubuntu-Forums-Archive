---
title: "How to get lcdproc to start at boot In Ubuntu 16.04?"
date: 2016-06-16
forum: Hardware
---

### Post by mtbdrew on 2016-06-16
New install of Ubuntu 16.04 with iMon LCD. Have set up the LCDd.conf and can manually start LCDd with terminal command. However it does start automatically at boot. There were no additional steps needed with 14.04, 14.10 or, 15.10 all was ready after loading lcdproc and configuring LCDd.conf file. Anyone know what is needed to get this to work at boot up?

Thanks
Andrew

Edited:

Found answer to my question in Mythbuntu forum:

[http://ubuntuforums.org/showthread.php?t=2323647](http://ubuntuforums.org/showthread.php?t=2323647)

Run this command:

sudo systemctl enable LCDd.service

---

### Post by RGilbert on 2016-11-13
The workaround at [Bugs]("https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/1597009") helped here.

"workaround by adding "service LCDd start" to /etc/rc.local."

---


---
title: "External Monitor Blank when Lock - Laptop is Shut"
date: 2017-08-22
forum: Hardware
---

### Post by handydandyhim on 2017-08-22
Alright y'all, 
I have searched quite a few resources out there on this topic and have gotten it about 80% working. My goal is to be able to ignore the event of closing the lid to my laptop and only use my external HDMI monitor. I have setup the **/etc/systemd/logind.conf** file to ignore the lid closing by uncommenting the HandleLidSwitch=ignore line. This allows me to close the lid and use the external monitor as the only display on the system. The problem is when I lock the desktop, it just turns to a blank screen and I'm unable to unlock it using the external monitor...I have to pull my laptop out of the desk and open it for it to show anything.

Here's the content of the config file:
```
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See logind.conf(5) for details.

[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
LidSwitchIgnoreInhibited=no
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#UserTasksMax=12288
```

I don't see any option to ignore closing the lid in the Xubuntu Power Manager. See attached screenshot.

Anyone face this issue?

---

### Post by gordintoronto on 2017-08-23
I think this has the answer:
[https://askubuntu.com/questions/362667/xubuntu-13-10-disabling-suspend-on-lid-being-closed](https://askubuntu.com/questions/362667/xubuntu-13-10-disabling-suspend-on-lid-being-closed)

---


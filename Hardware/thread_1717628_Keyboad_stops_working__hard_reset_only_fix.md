---
title: "Keyboad stops working : hard reset only fix"
date: 2011-03-30
forum: Hardware
---

### Post by arpoodle on 2011-03-30
Hardware: Dell XPS17

feef@hiro:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
feef@hiro:~$ uname -a
Linux hiro 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

Logitech K350 USB cordless keyboard.

Symptoms:
Periodically, the keyboard will stop responding. This affects both the Logitech keyboard and the laptop's own keyboard. 
No obvious triggers.  Seems to occur around when "home" is pressed, which acts as "select all", or pg-up/pg-dn. However, there's no evidence to suggest that these are causes.

No evidence of anything untoward in the logs.

Only a hard reset seems to fix it.

Mouse operations are unaffected.

System was working fine yesterday.  Haven't run any updates today.

Anyone got any ideas?

---

### Post by arpoodle on 2011-03-30
Have identified that unplugging and reconnecting the USB keyboard fixes the issue.

Will replace the batteries in the keyboard later today and see if that helps, although it's only a few months old, I'd expect them to last longer AND for the keyboard not to lock everything up if they are going flat.

---

### Post by cvog on 2011-05-20
I am having the same issue since upgrading to natty.The usb keyboard stops responding and needs o be reconnected. Has anyone  identified the issue?

Thanks,

Chris

---


---
title: "Suspend/hibernate problem on ASUS G53JW laptop"
date: 2011-02-06
forum: Hardware
---

### Post by Jorqn on 2011-02-06
Hello,

On my ASUS G53JW laptop..

Both suspend & hibernate lead to a blank screen with only cursor. I can only press "power" until the computer restarts.

As written in other threads, I have haded
SUSPEND_MODULES="xhci_hcd"
to both /etc/pm/config.d/unload_module and /etc/pm/config.d/00sleep_module

this has made things change: with hibernate, I now have to reboot the computer twice before I can start ubuntu. I also can get a turned off screen (but with still ventilators on), but It still won't wake up.

I have tried both s2ram and acpitool, but of course neither is working.

Does anyone have an idea?

Thank you
Jorqn

---

### Post by usercontrol on 2011-02-24
Try this:

[http://ubuntuforums.org/showpost.php?p=9180298&postcount=7](http://ubuntuforums.org/showpost.php?p=9180298&postcount=7)

Works for me and lot of latest asus notebooks (i have Asus N43JQ).

---


---
title: "Hibernation on low battery doesn't work"
date: 2009-03-04
forum: Hardware
---

### Post by m4lte on 2009-03-04
**SOLVED**

When the battery is critically low my laptop does not suspend even though I checked this option in the Power Management Preferences. The computer continues to run until it just switches off. The Panel Applet does indicate the low battery though.

In this post [http://ubuntuforums.org/showpost.php?p=5231019&postcount=13](http://ubuntuforums.org/showpost.php?p=5231019&postcount=13) it was recommended to set ENABLE_AUTO_HIBERNATION=1 in /etc/laptop-mode/laptop-mode.conf. I could not find this line. Do I need to add this line or has it been removed in recent ubuntu versions?

How can I get my computer to hibernate when the battery status is critical?

I'm using Intrepid 2.6.27-11 on a lenovo thinkpad R400.

---

### Post by broshe on 2009-04-20
Hello,
Here is what solved this problem for me:
Following pruch in [https://bugs.launchpad.net/bugs/186390](https://bugs.launchpad.net/bugs/186390),
I launched gconf-editor and set:
/apps/gnome-power-manager/general/use_time_for_policy (false)
/apps/gnome-power-manager/thresholds/percentage_low (15)
/apps/gnome-power-manager/thresholds/percentage_critical (12)
/apps/gnome-power-manager/thresholds/percentage_action (10)
/apps/gnome-power-manager/actions/critical_battery (hibernate)

Also, in settings->power management, activate hibernation on low battery option.

Everything works now.

Eli

---

### Post by m4lte on 2009-04-20
> **broshe said:**
> Hello,
Here is what solved this problem for me:
Following pruch in [https://bugs.launchpad.net/bugs/186390](https://bugs.launchpad.net/bugs/186390),
I launched gconf-editor and set:
/apps/gnome-power-manager/general/use_time_for_policy (false)
/apps/gnome-power-manager/thresholds/percentage_low (15)
/apps/gnome-power-manager/thresholds/percentage_critical (12)
/apps/gnome-power-manager/thresholds/percentage_action (10)
/apps/gnome-power-manager/actions/critical_battery (hibernate)

Also, in settings->power management, activate hibernation on low battery option.

Everything works now.

Eli

Wow, that helped. Thanks a lot. I didn't expect a solution any more.

---

### Post by farchumbre on 2009-07-19
it didn't work for me.
any suggestions?

---


---
title: "No battery indicator in 10.04"
date: 2010-08-01
forum: Hardware
---

### Post by tpg on 2010-08-01
I've just done a fresh install of 10.04 on my laptop, which had 8.04 previously. It seems to work nicely, except that there is no battery indicator in the panel. I've tried plugging/unplugging the lead and it doesn't seem to make any difference.

Any hints on how I can find out what's wrong please? Cheers.

---

### Post by alexshr on 2010-08-01
I had the same problem and installing gnome-power-manager solved my problem.

```

sudo apt-get install gnome-power-manager

```

---

### Post by yasmar on 2010-08-08
I had the same problem. I had to explicitly add it to the startup programs:
System --> Preferences --> Startup Applications
click on 'Add' and for the command enter 'gnome-power-manager'

However, I have reduced functionality over what I had before. In HH 8.04 I could hover the cursor over the battery icon and I would be informed how much time was remaining to charge/discharge the battery. Now I only get an indication of percentage charged.

There is some info here
[http://live.gnome.org/GnomePowerManager/FAQ](http://live.gnome.org/GnomePowerManager/FAQ)
and I tried toggling apps/gnome-power-manager/general/use_time_for_policy
in gconf-editor (it *was* checked), but it made no difference.

There is the suggestion that my ACPI bios may be 'broken', but it was working fine before the upgrade.

Any suggestions on how to recover this functionality of g-p-m would be greatly appreciated. 

Thanks.
(suspend and hibernate seem to work okay)

---


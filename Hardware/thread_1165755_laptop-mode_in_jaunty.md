---
title: "laptop-mode in jaunty"
date: 2009-05-21
forum: Hardware
---

### Post by cnolanAU on 2009-05-21
Has anyone else noticed that laptop-mode is no longer activated when changing from AC to battery (even though it is enabled in /etc/default/acpi-support)?  I need to manually run /usr/sbin/laptop_mode to have it detect that is should be active.  Not sure if it's just me.

I figure I can modify the /etc/acpi/[ac|battery|resume|start|suspend].d/90-hdparm.sh scripts to run /usr/sbin/laptop_mode instead of doing nothing if they detect that laptop_mode is enabled, but I'm not sure if this is the correct way to do it.  Is laptop-mode itself supposed to detect the power events directly, or does it rely on being called?

---

### Post by Barry Carroll on 2009-05-21
I enabled laptop-mode and then found that it was spinning down my drive way too much for my liking.  When I changed the idle timeout values they appeared to be ignored so I am leaving it alone for another bit until I can investigate it further.

---

### Post by cnolanAU on 2009-05-21
That sounds consistent with what I'm seeing.  It looks like laptop_mode doesn't get run with changes in power state, but the scripts that are run check to see if laptop mode is enabled, and if so they don't apply the default 'simple' hdparm settings.  So effectively, if you enable laptop mode, nothing manages the power settings (thus if you boot on battery, hdds will be always aggressively power-saving, if you boot on AC, hdds will be always on).

---

### Post by NESFreak on 2009-05-22
> **Barry Carroll said:**
> I enabled laptop-mode and then found that it was spinning down my drive way too much for my liking.  When I changed the idle timeout values they appeared to be ignored so I am leaving it alone for another bit until I can investigate it further.

Same here. Laptop mode just ignored whichever setting i passed to /etc/laptop-mode/laptop-mode.conf

Since there is no way of controlling the spin downs it does so every five seconds, probably screwing up my harddrive, apart from consuming an extra 10 watts according to powertop.

---

### Post by Barry Carroll on 2009-05-22
I also checked the drive's smart attributes and I could see that the Load_Cycle_Count was going up quickly.  So if the values in the conf file are ignored then where are they set?

---

### Post by cnolanAU on 2009-05-23
Seems like the easiest and safest option for now is to disable laptop mode by going to /etc/default/acpi-support and setting

```
ENABLE_LAPTOP_MODE=false
```

then rebooting.  This will go back to the 'default' behaviour of setting all hdd power management levels to 254 when on AC and to 128 when on battery (which should stop any excessive parking issues while on AC at least)

Interestingly, there are related bugs that have been open for quite a while on the laptop-mode-tools package that don't seem to have a resolution, I'll try to follow this up.

---

### Post by quoob on 2009-08-15
Any updated info on this matter?  (Alternatively, any hints on where to look for Ubuntu's policy on laptop mode?)

---

### Post by beruic on 2009-08-21
I ask the same.

Is the temporary fix still to edit all your /etc/acpi/*.d/90-hdparm.sh files, and turn laptop-mode off, or is there another way?

---

### Post by beruic on 2009-08-21
Just checked my /etc/default/acpi-support, and it seems like I have
ENABLE_LAPTOP_MODE=false

Should I try to switch it on, or is the current recommendation to leave it off?

I am tired of my hard disk load cycling so much.

---


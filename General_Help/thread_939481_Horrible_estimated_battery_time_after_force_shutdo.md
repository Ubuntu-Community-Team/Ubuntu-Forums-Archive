---
title: "Horrible estimated battery time after force shutdown (and disk check?)"
date: 2008-10-06
forum: General Help
---

### Post by MilchFlasche on 2008-10-06
Hi, I'm using Eee PC 701 (4G) and running Ubuntu 8.04.1 on it. I found that yesterday after I had had to turn off the laptop forcibly and boot the machine without disk check, the estimated battery time of gnome-power-manager went crazy. Please take a look at the attached screenshot: on the top-right, the pop-up shows that there remains "452150 hours" until fully charged and the power can sustain "83332 hours and 30 minutes". Quite improbable, isn't it?

Is there any config file I should delete and rebuilt? Because when I did a fsck after I have found this, there seemed to be messages about multiple claimed cluster of a file called "gnome-701-recharge" or something, but I skipped that and just pressed y to fix (I'm not so sure what I did then).

---

### Post by MilchFlasche on 2008-10-06
I've run "acpi" in command line, and I got

Battery 1: discharging, 40%, rate information unavailable.

And I have checked my /proc/acpi/battery/BAT0/state, it shows:
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      30 mAh
present voltage:         7343 mV

I guess it might be that the line "present rate: unknown" is causing wild numbers for estimated battery remaining time? But why can't my system detect the right present rate any more?

---


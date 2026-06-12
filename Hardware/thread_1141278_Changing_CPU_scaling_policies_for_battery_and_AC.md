---
title: "Changing CPU scaling policies for battery and AC"
date: 2009-04-28
forum: Hardware
---

### Post by achinton on 2009-04-28
Hi,

Setting up CPU scaling to try to get my battery performance improved, I've been following instructions such as [these]("http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You") to get it going. All fine, until the final step:

> To change the default head back into your terminal and type:

gconf-editor

From there head to apps -> gnome-power-manager -> cpufreq. Find the settings policy_ac and policy_battery and change them to whichever setting you want for the default.

The problem is simple: there's no such setting, and indeed, no section called "cpufreq" under "apps > gnome-power-manager".

What am I missing? Has this changed for Jaunty? Where did the settings go?!

Thanks for any help.

---

### Post by onero on 2009-04-29
I would also like to know the answer to this, as I also have no cpufreq settings in my Jaunty install. Has the way to set this changed? How do I set the default governors for battery and AC power? Thanks!

EDIT: Apparently this feature was taken out of gnome-power-manager: [http://ubuntuforums.org/showthread.php?t=971578](http://ubuntuforums.org/showthread.php?t=971578)

---


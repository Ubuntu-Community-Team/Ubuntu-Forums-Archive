---
title: "Keep Laptop Display Output Active (External Monitor)"
date: 2010-08-13
forum: Hardware
---

### Post by TrendyDark on 2010-08-13
I frequently use my small HDTV as a monitor for my laptop (useful for watching films, etc). Ubuntu will pick up the second monitor, and displays everything just great for me (well, as well as Windows 7 lol). The only issue I'm having is getting my computer not to go to sleep when I close the laptop's lid.

In the power management application there are all the right settings for fixing this (keeping the hardware all running while plugged into a power source), except for the screen output. There's no option to keep my screen ON when the lid is closed!

Any ideas?

---

### Post by aidan_walton on 2011-06-14
1.When on AC Power, do nothing when laptop lid is closed:  
gconftool-2 -t string -s /apps/gnome-power-manager/buttons/lid_ac nothing  

  2.When on Battery Power, do nothing when laptop lid is closed:  
gconftool-2 -t string -s /apps/gnome-power-manager/buttons/lid_battery nothing

---


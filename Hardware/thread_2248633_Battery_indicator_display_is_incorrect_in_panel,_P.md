---
title: "Battery indicator display is incorrect in panel, Power Settings"
date: 2014-10-15
forum: Hardware
---

### Post by cturnes on 2014-10-15
I'm running Ubuntu 14.04 on my laptop, and I recently installed the Unity Tweak Tool to change some of the fonts for the unity desktop.  I don't actually care about the fonts that much, it was just to make one application that I am using look a little better (it uses the system fonts).  

Since I installed it, I've noticed that the battery meter on the panel doesn't update its display, even when plugging and unplugging the power source.  I tried some of the general troubleshooting steps listed here (I'm aware that thread is for a different issue, but there are some generic fixes in there), but no dice:

[http://askubuntu.com/questions/473784/battery-indicator-has-disappeared-from-gnome-panel](http://askubuntu.com/questions/473784/battery-indicator-has-disappeared-from-gnome-panel)

I do notice that
```
[FONT=Ubuntu Mono]pkill -f indicator-power-service[/FONT]
```
corrects the display once the indicator-power-service restarts, but it still doesn't update.

Does anyone have any ideas?

---


---
title: "gnome-panel freeze"
date: 2008-07-14
forum: General Help
---

### Post by bayonetblaha on 2008-07-14
My Hardy panel is running only a window list, notification area, and clock.  Clicking on the clock to display different locations and weather results in a clock freeze every time.  Clock is stuck in the depressed appearance after being clicked. When I run "killall gnome-panel" the panel restarts without the battery or network manager in the notification area.

---

### Post by pauper on 2008-07-18
You can bring up Power Manager and Network Manager applets by:

```
gnome-power-manager &
nm-applet &
```

In my experience, if I kill gnome-panel I always have to start NM applet
manually, but PM restarts on its own.

Just a thought, sometimes, when my laptop's uptime goes beyond several days, I 
got some random black pixels near notification area. So instead of killing the
panel I simply repaint it by:

```
xrefresh -geometry 1280x24+0+0
```

---

### Post by prshah on 2008-07-18
> **bayonetblaha said:**
> 
Clicking on the clock to display different locations and weather results in a clock freeze every time.  

I have the same problem, only in mine the freeze is intermittent; usually it works, with a delay of upto 5 seconds, but sometimes, it just locks up tight. I ended up removing the additional places and timezones from the clock; it really bugging to want to check the calendar but end up restarting gnome/panel/system.

---

### Post by Jad on 2008-08-04
Do you have google calendar in your evolution calendar?

---


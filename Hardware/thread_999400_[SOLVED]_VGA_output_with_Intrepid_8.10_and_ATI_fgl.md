---
title: "[SOLVED] VGA output with Intrepid 8.10 and ATI fglrx driver"
date: 2008-12-01
forum: Hardware
---

### Post by PilotJLR on 2008-12-01
Hi everyone,
I had to do some digging to get this info together (probably because I'm new to ati-config)... I'm posting it now in case it helps out anyone.

**Problem:** I put Intrepid Ibex 8.10 on my laptop, which has a basic ATI video card. The fglrx driver works quite well and I have good compiz effects... but I needed a way to turn on the VGA output without restarting X. This is mainly because I sometimes need to use a projector and present powerpoints or other things. Restarting X is quite a hassle, especially if a lot of apps are open.

**Solution:** The instructions below work if you are using the fglrx driver. The radeon driver should work with only xrandr commands, which are in various threads in the forums.


Step 1 - Use aticonfig to write an inital config to xorg.conf:
```

sudo aticonfig --initial

```
This step appears to be mandatory with the aticonfig tool, though X currently does not need a conf file. I did this step, then restarted X, and did not notice any ill effects!


Step 2 - Plug in a projector to the VGA port on the laptop and find the port's name:
```

aticonfig --query-monitor

```
On my laptop, the laptopscreen is called "lvds" and the VGA port is "crt1". I don't know if this is the case with all laptops. If your VGA port is not called "crt1", make a note of it!


Step 3 - Take the screen resolution down to a projector-friendly resolution, like 1024x768 or 800x600:
```

xrandr -s 1024x768 

```


Step 4 - Turn on the VGA port (and keep the laptop screen on too):
```

aticonfig --enable-monitor=lvds,crt1

```

At this point, your VGA port and screen should both be at 1024x768 resolution and working.


To make this a bit easier, I put these last 2 commands into a script and made a launcher icon on my toolbar. I just need to click the icon on the toolbar, and I'm ready for a presentation. I like the 1-click switchover, as opposed to choosing the script in a terminal or manually typing out these commands.

```

#!/bin/sh
#requires fglrx driver
##
xrandr -s 1024x768 
aticonfig --enable-monitor=lvds,crt1

```


I hope this helps!

---


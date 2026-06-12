---
title: "[HowTo] Get (partial) brightness control on most Samsung notebooks/netbooks!"
date: 2011-07-05
forum: Hardware
---

### Post by thattypicalnerd on 2011-07-05
Make a script that contains the following-

```
#!/bin/bash
gksudo gedit /sys/class/backlight/samsung/brightness
```

**What this does-** 

It basically opens the file *brightness* found in */sys/class/backlight/samsung* as root in gedit. 

Enter your password when prompted, and open the script. You should be looking at a file that has one number in it, from 0 to 7. You can edit the brightness value from here! When you input the value you want, Save the file, and hit cancel to anything that gedit says. 

I took this a step further, and had this start up when I log in, and also created a shortcut on a panel. 

This is to serve as a temporary solution until I can get the Gnome backlight control working.

---


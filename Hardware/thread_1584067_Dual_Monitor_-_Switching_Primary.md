---
title: "Dual Monitor - Switching Primary"
date: 2010-09-28
forum: Hardware
---

### Post by Taollan on 2010-09-28
I have setup a dual monitor system with my laptop and a ViewSonic VX2255wmb external VGA monitor in Kubuntu 10.04.  Essentially everything with the dual monitor works great except my "primary" monitor becomes the external VGA, with the desktop extended to my laptop monitor.  I would much rather my primary monitor be the laptop monitor, but am stuck figuring out how.  I have search the ATI Catalyst Control Center for an option to flip this, but to no avail.  I tried:
aticonfig --swap-monitor
And got:
Error: option --swap-monitor is not supported when RandR 1.2 is enabled!
I then found this post on how to disable Randr:
[http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)
but the disabling of Randr never persisted on restart of X, and I am not sure disabling Randr would be the best solution anyhow.  Additionally I tried the command:
xrandr --output LVDS --primary
But this doesn't do anything that I can tell (net even an error) and nothing has changed on restart of X.
So, does anyone have any advice on how to proceed from here?  I would greatly appreciate it.  
Oh, and my laptop is a HP Pavilion dv7-1245dx, and it is running an ATI Radeon HD 3200 using fglrx drivers.

---


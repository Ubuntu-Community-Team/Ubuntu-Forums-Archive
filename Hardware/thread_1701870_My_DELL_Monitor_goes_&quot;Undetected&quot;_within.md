---
title: "My DELL Monitor goes &quot;Undetected&quot; within 10.10!"
date: 2011-03-07
forum: Hardware
---

### Post by Saurabhdua on 2011-03-07
Hello Folks!

Using Ubuntu 10.10. My Dell Monitor continues to remain "Undetected" albeit my software updates, Ubuntu has received till date!?

Iam not able to maneuver any of the listed parameters within the "Monitors" under System>>Preferences.

Refer to the attached screenshot please & help me change the "Monitor Resolution" to 1024X768.

At present, it is struck to 1440X900(16:10)...!!?

---

### Post by nomko on 2011-03-07
How does your xorg.conf look like?

---

### Post by Saurabhdua on 2011-03-07
Hello Nomco!

What do you mean by that? Please ellaborate..!?

---

### Post by MartinFernando1993 on 2011-07-06
My resolution is at 800x600 and the refresh rate is at zero. The xrandr command in terminal shows this:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
```
When I open xorg.conf, it's blank. I'm running Ubuntu 10.10 with [Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)] integrated intel graphics.

---


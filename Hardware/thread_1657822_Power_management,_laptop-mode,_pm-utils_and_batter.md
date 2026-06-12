---
title: "Power management, laptop-mode, pm-utils and battery"
date: 2011-01-01
forum: Hardware
---

### Post by 3602 on 2011-01-01
Recently I discovered that my hard disk would spin up and down continuously while under battery power. After reading whatever little info there is, I installed:
```
laptop-mode-tools
```
Which removed:
```
pm-utils
```
Reboot. Upon reboot, I happily found out that the disk is no longer clicking, however under Power Management I found no Suspend nor Hibernate. Google brought me to this:
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)
As per posts #11, #13 over there, I installed the re-rolled *pm-utils* and reboot. Now the two functions are back, but I found another problem.
During the day, my battery consumption rate was (at the time I viewed it) 7 watts. I had 6 hours of battery back then. But that was a split-second check, didn't monitor it for long.
After installing this re-rolled package, I had a consumption of 17 watts and 2.5 hours of battery. Now, during the day, I had my nVidia card disabled: [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
And that brought down the consumption a lot. However it was apparent that the card didn't stay disabled and will come back on-line every time I boot/reboot. Yet even after disabling the card, I get, at minimum, 10 watts of consumption, never that 7 watts during the day.
I even uninstalled laptop-mode-tools, uninstalled the re-rolled pm-utils and installed the "standard" pm-utils. Even then my consumption would be at 10 watts.
Basically, what's up.

---

### Post by 3602 on 2011-01-01
Wait a minute. I just unplugged the power cable for a split-second check. I saw 6 watts.
What the heck? Is power supposed to fluctuate this much? When I just boot I see 20 watts but it drops to 17 after several minutes but...

EDIT: It's all fine and dandy. The consumption rate is not constant. I get it.

---


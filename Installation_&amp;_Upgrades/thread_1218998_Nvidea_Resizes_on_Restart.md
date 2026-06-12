---
title: "Nvidea Resizes on Restart"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by sundeniro on 2009-07-21
Hi Guys

Total Newbie here.

After much messing around I eventually got the nvidea settings tool to give me full options for setting resolution (by finding the frequency ranges for the monitor and changing xorg.conf)

Now this is working and I can set desktop to an acceptable size I find I have 2 issues.

Firstly, When i restart the system the screen resets to 800*600. I change the settings by using a terminal and sudo nvidea-settings so that I can save changes to xorg.conf ok but it still resets on reboot.

Secondly, under system>preference>appearance>visual effects if I set normal or full my windows loose their borders and terminals become unusable as they are just white squares. Retuning this setting to none allows me to use the system.

I have lates ubuntu downloaded 2 days ago and have run all updates.

Graphics Card is GeForce4 MX 440 with AGP8X (connected via AGP4X)

Hope someone can help me out

---

### Post by wojox on 2009-07-21
open a terminal :


```
gksudo /usr/bin/nvidia-settings
```

edit and save that way.

Second you may have to install compiz windows manager or something like that for your border issues?

---

### Post by sundeniro on 2009-07-21
Thanks for the suggestion gave it a try but no joy:(

---

### Post by sundeniro on 2009-07-21
managed to solve the resolution thing

Solution was set everything as I had before then go to System>preferences>display choose no when it asks to use nvidea's console and then choose correct settings and apply and this time it sticks I have no idea why though.

---

### Post by sundeniro on 2009-07-22
think I should list problem 2 in a seperate threasd

---


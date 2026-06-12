---
title: "Monitor resolution not saved on reboot"
date: 2018-03-08
forum: Hardware
---

### Post by sugarcrisp on 2018-03-08
I'm running 17.10 on an Asus K501U laptop.  I have it connect to a Sharp Aquos "LC -40LE265X" TV using an HDMI cable.  When I reboot my laptop (or logout and back it) it will automatically connect to the TV with maximum resolution (1920x1080 (16:9)).  This resolution makes everything too small.  I manually change it to (1369x768 (16:9)), which works well for my application.  Unfortunately, it reverts to 1920x1080 on every reboot/login.  I've figured out a work around, by creating a bash script using xrandr that I run at startup that will change it to 1369x768.  This seems to work, but I would like to know if there is a permanent fix that can be applied?

---


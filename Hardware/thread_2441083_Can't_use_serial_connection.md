---
title: "Can't use serial connection"
date: 2020-04-19
forum: Hardware
---

### Post by boydhako on 2020-04-19
Anybody know how to stop agetty from hording ttyS0? 

I have a Raspberry Pi hat that uses serial via the GPIO. However, I can't connect gpsd to ttyS0. And if I'm able to successfully minicom in to S0 it acts that like it's refreshing at a berserk level and I occasionally see something that looks like a "Login:" prompt.

---

### Post by him610 on 2020-04-21
Wow! It it is my guess that not many forum participants have all of these devices.
A Raspberry Pi. Which model? 
A Pi Hat. I have one of those - not a GPS Hat though.
GPSD. Do you also have a GPS device? I have one of those - Prolific PL2303
Minicom. Don't know anything about that. Found this on the minicom website 'minicom is a serial communication program that connects to devices through a GNU/Linux PC's serial ports.'

Which verson of *buntu?

Added: Found this page related to minicom, [https://help.ubuntu.com/community/Minicom]("https://help.ubuntu.com/community/Minicom")

Please provide some more information about your setup - both hardware and software. Need to be patient though, it has been a few years since I worked with any GPS applications.

If I can duplicate your setup, maybe we can figure something out.

---

### Post by #&amp;thj^% on 2020-04-21
> **boydhako said:**
> Anybody know how to stop agetty from hording ttyS0? 

Yes a lot of information needed to inform you with a better experience.
****Please follow him610 advice first, and use my post as a last resort.**
But what I see and guess is, You can probably shut down the getty process on /dev/ttyS0, as it does not seem to be doing anything useful right now. To do that, these commands might be the simplest solution:
```

systemctl stop serial-getty@ttyS0.service
systemctl disable serial-getty@ttyS0.service
```

The first command tells systemd to stop trying to start the process until the next reboot, the second command will persistently mark it as disabled.  
you should also check your boot options: if console=ttyS0 is listed in there, systemd will automatically generate a getty process on /dev/ttyS0. **_**Note: This is for Ubuntu on a PI4 and not tested with Raspbian. _**

---


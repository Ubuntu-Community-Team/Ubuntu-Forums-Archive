---
title: "Asus VivoBook - nvidia gpu not working"
date: 2018-11-01
forum: Hardware
---

### Post by s0viet on 2018-11-01
Hello,

I have troubles with my GPU in Asus Vivobook. I have dual gpu system (Intel and nvidia mx 130). As I was not able to switch between gpus, I have installed nvidia gpu drivers. Now I have 4 drivers: 3 from nvidia (390, 396, 410) and 1 from Nouveau. Currently, no matter which driver I choose, the resolution doesn't work (maximum is 640, not FHD), also I cannot use nvidia X server settings. Any tips how to make everythig work?

@Edit:

To be more precise: 
[https://askubuntu.com/questions/732854/dual-monitor-not-working-intel-graphics-nvidia-960m](https://askubuntu.com/questions/732854/dual-monitor-not-working-intel-graphics-nvidia-960m) <-- been there, done that - still not working
after entering nvidia-settings from terminal, i have an error - Unabled to load info from any available system

@Update
OKay, i just manually added 1920x1080 res with xrandr, but nvidia stil doesnt work

@Update 2
```

Building initial module for 4.15.0-38-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-410.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-38-generic (x86_64)

```
It is an error I am getting when I install the drivers or try to dpkg-reconfigure

---


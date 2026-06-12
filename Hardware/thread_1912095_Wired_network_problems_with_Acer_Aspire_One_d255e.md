---
title: "Wired network problems with Acer Aspire One d255e"
date: 2012-01-20
forum: Hardware
---

### Post by MarsMartianMan on 2012-01-20
I've recently installed Ubuntu 10.4 on my Acer Aspire One d255e, it installed with no problems. Prior to installation, I researched compatibility and hardware problems, of which there were many. After following the guide written here: [http://ubuntuforums.org/showpost.php?p=9446984&postcount=6]("http://ubuntuforums.org/showpost.php?p=9446984&postcount=6")

I managed to get the ethernet controller to work, and proceeded to download system updates. I also downloaded drivers to fix the wireless internet card, and the SD card reader. Everything was working fine even after installing more drivers. I then restarted the computer, and it still worked fine.

After the third restart, the ethernet controller ceased to function. I tried two different networks, with two different cables, nothing worked. I then tried, in terminal:
 
```
sudo modprobe atl1c
```

To see if that would fix it, however it did not.

I had moved the compressed files containing my drivers into a different folder (they were previously on my desktop, when I installed them via terminal), but I don't know how that would cause a problem. So far I have no idea what could be preventing the connection from functioning properly. I'm currently typing this from the very same connection that the netbook will not detect, so I know at least this works.

EDIT: I tried reinstalling the drivers for the ethernet controller, and it seems to have fixed it for now. I'm going to restart the netbook to see if it still works. However, I'm still unaware of what caused the problem. Can anyone figure it out?

---


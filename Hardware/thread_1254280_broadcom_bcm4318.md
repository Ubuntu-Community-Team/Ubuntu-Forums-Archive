---
title: "broadcom bcm4318"
date: 2009-08-31
forum: Hardware
---

### Post by syron1988 on 2009-08-31
Hello guys,
 
I hope I do not make a post, which is already existing. I was wondering if anybody got a real solution for the bcm4318 wireless card. 
 
Once I installed Ubuntu and it worked without usung ndiswrapper, after I activated it, it was working pretty good. Unfortunately it wasn't available anymore in my hardware list. So I was searching around on different forums, even the ubuntuforums.com forum, but I didn't find any solution, which is working.
I installed ndiswrapper, downloaded a driver, which was recommended in this forum and I installed it via sudo ndiswrapper -i bcm43.inf or whatever the driverfile name was called.
After that I was able to find the wireless modems around my notebook, but I was unable to login to them. I have a router at home, to which I can connect with another laptop of mine, but with the ubuntu notebook, it's impossible. ubuntu asks me for the password, but it repeats it like 10 times, then it disconnect me from the network.
 
Did anyhave have the same problem and got a solution? I appreciate each type of help. Thank you very much.
 
Regards

---

### Post by sergiom99 on 2009-08-31
I think the problem is Network Manager (which has been reported as broken in Jaunty).
Most Broadcom cards dont need ndiswrapper and window$ INF files. The latest kernels have new broadcom drivers in them. To install the new drivers simply hook up your ethernet cable. Update. Reboot. Then go System > Administration > Hardware Drivers and check "Broadcom STA Wireless Driver." If you've already installed the broadcom drivers with my script simply run the uninstaller, reboot, and then follow the previous steps.

And install wicd instead of Network manager. Works WAY better.
```
 sudo aptitude install wicd
```

Good luck!

---


---
title: "Screen Shuts Off on Boot (Possible graphics issue?)"
date: 2011-08-09
forum: Hardware
---

### Post by srozzman on 2011-08-09
Hi, long time lurker here... anyways,

Due to choppy video playback on the newest fglrx drivers, I tried to revert back to the opensource drivers with the commands in this guide - [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) , specifically this part, Problem: Need to fully remove -fglrx and reinstall -ati from scratch.  

As a result, upon starting up the computer, I get a purple screen, then it flashes the loading animation, then the screen turns off.  I have no idea what is going on, and as the screen turns off, I cannot see the output of any commands.  

Any help is appreciated.

Machine Specs:
AMD 4000+ x2
4gb Ram
Raedon 2600xt
1080p LG LED Monitor
Ubuntu 11.04 64-bit

---

### Post by papibe on 2011-08-09
Maybe this [thread]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=black") would help.

Regards.

---

### Post by srozzman on 2011-08-09
Just solved it - 

My Solution - 

Ctrl - alt - F1 into terminal
Remove all xorg.conf
   sudo apt-get install --reinstall xserver-xorg-core
reboot

I dont know which of this fixed it, but it did. Thanks

---


---
title: "broadcom wireless 4306 not being found"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by worp on 2006-01-03
so i installed ndiswrapper got the driver all set:

danny@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

now when i run iwconfig nothing shows up for wlan0 and it the device does not show up in the network tools either.. it does show up in the device manager so the driver works.. not sure if it is not turning on or what.. the light on my laptop for wireless is on and i have it auto start on boot up.. any suggestions? 

having a 50 foot network cable dragging around is not so fun anymore lol..

---

### Post by kperkins on 2006-01-07
Did you do a 'ndiswrapper -m' as well as an install?
That modprobes it so the kernel knows it's there.
Did you see this thread [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) ?

---


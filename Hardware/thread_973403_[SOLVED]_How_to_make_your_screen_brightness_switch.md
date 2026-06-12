---
title: "[SOLVED] How to make your screen brightness switches work on ASUS M70 M50"
date: 2008-11-06
forum: Hardware
---

### Post by tvtech on 2008-11-06
A quick and simple how to, This tutorial is for all Asus M50  and Asus M70 models with ambient light sensor.  

It was tested specifically on an Asus M70VM-C1
 
This how too will enable your LCD light switchs on your keyboard, so you can manually change the brightness of your LCD. This will disable your ambient light sensor if it in fact did work on your initial install of Ubuntu 8.10, 8.04

ok so for those of you scared of terminal this is easy to do and you can easily copy and paste.  


Go to [COLOR="Lime"]Applications>Accessories>Terminal[/COLOR]

[COLOR="Red"]Install sysfsutils[/COLOR]
```
sudo apt-get install sysfsutils
```
[COLOR="Red"]Then go to and edit the following file[/COLOR]
```
sudo gedit /etc/sysfs.conf
```
[COLOR="Red"]At the end of the opened file add the following line as typed below[/COLOR]
```
devices/platform/asus-laptop/ls_switch=0
```
[COLOR="Red"]Reboot[/COLOR]


This will enable your keyboard LCD brightness toggle switches to function on your next reboot. 

special thanks for this tutorial go to everyone in the [This thread]("http://ubuntuforums.org/showthread.php?t=788540")
and [This Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251278")

---


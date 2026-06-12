---
title: "Keyboard and Mouse event logger for linux"
date: 2013-10-23
forum: Hardware
---

### Post by Gopal_Sharma on 2013-10-23
Hi, 

I have written a program to log keyboard and mouse events. For this I have used device files from directory **/dev/input/**. Its works fine. But I have to log events coming from a remote Keyboard/Mouse also.

Means I am using tightvnc to access that machine on which logger is running. But in this case logger is not logging events coming from vnc client or remote input device.

I have go through the vnc source code but could not find much to this problem.

Can anyone tell me how I can log keyboard/mouse events coming from a remote input devices?

Thanks,

Gopal Sharma

---


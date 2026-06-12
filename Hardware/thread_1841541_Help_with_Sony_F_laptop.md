---
title: "Help with Sony F laptop?"
date: 2011-09-09
forum: Hardware
---

### Post by OLinux on 2011-09-09
Hi everyone, I'm looking for advice. So far my experience with Ubuntu on my Sony F laptop hasnt been the most exciting and hopefully someone can help me tweak my settings to better the performance.

First, I have installed the latest nvidia drivers on the laptop yet I cant control the screen brightness with the fn shortcuts. Besides that, the colors on the screen look just plain dull and bland. Its hard for me to work like this. There is a brightness controll on the nvidia control panel but that barely helps and makes things look worse actually. Are there any config files I can tweak?

Second, for some reason my download speeds when I download things from the application center or for example trying to download google chrome takes a long time. The laptop is definitely faster on my Win 7 partition. I even ran a speedtest dot net test and my speeds didnt show up as slow at all so not sure what is wrong. Something is limiting my download speeds. Any files I can tweak for this issue?

I really want to enjoy Ubuntu but not sure if these issues are just with my laptop?
Am I better off installing a different linux distro that has better compatibility?

---

### Post by mörgæs on 2011-09-10
For the Nvidia problems, I would try this thread:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

If downloading from Software Centre is slow, it is not necessarily a problem on your computer. As a first test, try to change repository mirror.

---

### Post by OLinux on 2011-09-14
Thanks, that thread didnt really help much with my issue. Its weird some days the screen looks brighter than others. Maybe there is a way to disable auto brightness in ubuntu?

---

### Post by mörgæs on 2011-09-15
I don't know how to solve the brightness problem, but regarding the speed some people get a big improvement by disabling IPv6. Have not tried it myself, so I can not give a clear recommendation. 

By the way, which release of Ubuntu are you using?

---

### Post by Toz on 2011-09-15
With nVidia cards, you can sometimes get control of the brightness functionality by using the EnableBrightnessControl parameter. 

If you have an **/etc/X11/xorg.conf** file, add the following to the Devices section:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```

If you don't have an /etc/X11/xorg.conf file, you'll need to create **/usr/share/X11/xorg.conf.d/20-brightness.conf** with the following content:
```
Section "Device"
   Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Restart X (logout and back in again).

---


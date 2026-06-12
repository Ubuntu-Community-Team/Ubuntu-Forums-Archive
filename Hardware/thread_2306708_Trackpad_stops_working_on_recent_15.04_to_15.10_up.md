---
title: "Trackpad stops working on recent 15.04 to 15.10 upgrade"
date: 2015-12-17
forum: Hardware
---

### Post by glenmatthewwilson on 2015-12-17
I just upgraded from 15.04 to 15.10 on my Lenovo ThinkPad. I can move the cursor for a few seconds once I login to the Unity GUI, but then it stops. I can press the trackpad to get the left and right mouse clicks to work, but the cursor does not move, and scrolling does not work. 

I was able to regain some functionality by removing the psmouse module and then reloading it, following the guidelines on another thread. However, the functionality of the trackpad is greatly reduced after this. I am unable to do two-finger scrolling, and the sensitivity is greatly decreased. 

How can I restore reliable trackpad behavior? This was not an issue in 15.04. 

Thank you!

---

### Post by deepakdeshp on 2015-12-18
[COLOR=#000000]Grub gives option to boot from your old kernel when you boot from recovery mode . Boot from your old kernel and try.[/COLOR]


[COLOR=#000000]Otherwise please try installing latest Kernel. It may support the mouse. But [/COLOR][COLOR=#ff0000]it may break[/COLOR][COLOR=#000000] the system if some vital hardware isnt supported.[/COLOR]

[http://www.ubuntumaniac.com/2015/11/...kernel-43.html]("http://www.ubuntumaniac.com/2015/11/how-to-upgrade-to-linux-kernel-43.html")

---

### Post by glenmatthewwilson on 2015-12-18
I found the following fix by googling around some. It seems to reload the working version of the psmouse module. 

```

sudo rmmod psmouse 
 sudo modprobe -v psmouse insmod /lib/modules/3.16.0-34-generic/kernel/drivers/input/mouse/psmouse.ko 

```

I need to figure out how to have this change incorporated into the boot up sequence, but it works! Hopefully it can be of use to anybody else with a similar issue.

---


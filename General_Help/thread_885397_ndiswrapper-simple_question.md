---
title: "ndiswrapper-simple question"
date: 2008-08-10
forum: General Help
---

### Post by Comzee on 2008-08-10
I used ndiswrapper to install a windows driver for my wireless card, everything works fine. I use the command ```
modprobe ndiswrapper
``` to initialize wlan 0 (ie the wireless card).

But every time I reboot I have to use the same command to initialize it. Is there a way to make it auto initialize my wireless card on boot-up. 

Thanks in advance :D

---

### Post by cdtech on 2008-08-10
Try adding "ndiswrapper" to your /etc/modules file:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ndiswrapper
loop
lp
rtc
sbp2
fuse
k8temp
powernow-k8
```

---

### Post by Comzee on 2008-08-10
Never knew about that file, kewl stuff, thanks !!

it worked btw...

---

### Post by cdtech on 2008-08-10
Great...

---


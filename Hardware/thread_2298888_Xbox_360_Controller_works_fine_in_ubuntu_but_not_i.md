---
title: "Xbox 360 Controller works fine in ubuntu but not in steam"
date: 2015-10-14
forum: Hardware
---

### Post by Wagadoo on 2015-10-14
Hi, I have an xbox 360 controller that is installed and works great in Ubuntu 14.04. The problem is when I try games in Steam, the right joystick drifts to the right and doesn't respond to moving left. Has anyone seen the problem before? I haven't been able to find anything after much Googling. Any help would be appreciated. Thanks in advance.

---

### Post by darksim2 on 2016-03-23
I've had the same problem using an Xbox 360 controller in Steam through PlayOnLinux. I managed to get the problem partially solved (the control sticks work properly, but button mapping is interpreted incorrectly by something other than the driver) by getting the ubuntu-xboxdrv through:

```

sudo apt-add-repository ppa:rael-gc/ubuntu-xboxdrv
sudo apt-get update && sudo apt-get install ubuntu-xboxdrv

```

From there you just have to either run

```

sudo rmmod xpad
sudo xboxdrv -s

```

or blacklist xpad entirely (which I don't recommend until you've gotten ubuntu-xboxdrv working the way you want). This, on my end, solved the problem of the joystick drift but results in some strange button mapping issues where running xboxdrv without -s shows the driver recognizes the button mapping properly but somehow the input is still being misinterpreted somewhere along the line before being run by the game itself.

---


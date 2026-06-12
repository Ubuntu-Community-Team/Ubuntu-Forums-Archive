---
title: "Testing xbox 360 controller"
date: 2010-03-14
forum: Hardware
---

### Post by Jordanwb on 2010-03-14
I've found that the TrackMania series works damn well under Linux. So I want to see if I can get my Wireless 360 controller for Windows working under linux, and in turn through wine. I've modprobed the xpad module and turned on my controller. How would I find out if the controller is working? In [this section]("https://help.ubuntu.com/community/Xbox360Controller#Updating%20the%20drivers") it says to install jscalibrator for calibration but this package doesn't exist. I'm running Lucid Lynx.

Running "cat /dev/input/js0" causes unknown characters to be displayed whenever I press the button or axis on my controller.

---

### Post by botnet on 2010-04-16
On Ubuntu 9.10 there is a package joystick.

```
sudo apt-get install joystick 
```

it has the commands jstest and jscal.

```
jstest /dev/input/js0 
```

I'm using it to connect to a wired xbox 360 controller and it seems to output similarly to [xboxdrv]("http://ubuntuforums.org/showthread.php?t=825464") (the userspace alternative to the xpad kernel module).

---

### Post by Jordanwb on 2010-04-16
Okay so the xpad module is working. Now to get it working in Wine. If possible.

---

### Post by norseman-has-a-laptop on 2010-04-16
there should be a drive out there for the controller

---


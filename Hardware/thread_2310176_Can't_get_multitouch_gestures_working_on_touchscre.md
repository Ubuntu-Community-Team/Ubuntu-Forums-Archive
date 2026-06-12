---
title: "Can't get multitouch gestures working on touchscreen"
date: 2016-01-16
forum: Hardware
---

### Post by satan3 on 2016-01-16
Hi

So i'm having trouble getting full multitouch gestures on the touchscreen of my Dell Inspiron 7537, running windows 8.1 and Ubuntu Mate 15.10 dual boot.  At the moment it works but only allows a one-finger touch gesture, like a mouse.    It's listed as 

```
Bus 001 Device 004: ID 04f3:0201 Elan Microelectronics Corp. Touchscreen
```

using lsusb.  Before getting to Ginn, Geist, touchegg and other multitouch gesture programs and how to get them to actually work, I found information fairly thin on the ground, for the average user, about basic tests that can be performed that might be helpful in finding more information about the touchscreen and how it's performing. The ubuntu wiki section on multitouch was helpful to a point but beyond that there's not much else. 

for example in the checkignMTDevice section, as suggested, i tried 

```
sudo mtdev-test /dev/input/event11
```

where event11 is the touchscreen.  A chunk of the output being: 

```
   ABS_MT_SLOT
   ABS_MT_TOUCH_MAJOR
   ABS_MT_TOUCH_MINOR
   ABS_MT_ORIENTATION
   ABS_MT_POSITION_X
   ABS_MT_POSITION_Y
   ABS_MT_TRACKING_ID
01524ce430ae 00 3 0039 37
01524ce430ae 00 3 0035 650
01524ce430ae 00 3 0036 1081
01524ce430ae 00 3 003c 650
01524ce430ae 00 3 003d 1081
01524ce430ae 00 1 014a 1
01524ce430ae 00 3 0000 650
01524ce430ae 00 3 0001 1081
01524ce430ae 00 0 0000 0
01524ce430b5 00 3 0034 1

```

which i don't understand any of, except that it's working and the values change if i apply more fingers to the screen or take them off, and the ubuntu wiki doesn't offer anything either.  

I tried using touchegg to not much success though i'm still working on it, GEIST and its gui Geistview detected both mouse and touchscreen but there was no change with how the touchscreen performed.  Ginn i have yet to try.  

The clickpad supports multitouch gestures as i can zoom in and out of maps for example, in the familiar way.

So if anyone has any ideas how to proceed from here i'd love to hear them. Even pointers to what the output from mtdev-test means or things like this would be a victory.

Thanks in advance for your suggestions

---


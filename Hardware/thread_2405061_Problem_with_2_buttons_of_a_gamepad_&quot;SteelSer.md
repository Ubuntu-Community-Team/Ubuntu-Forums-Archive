---
title: "Problem with 2 buttons of a gamepad &quot;SteelSeries Stratus XL&quot; in Ubuntu 18.10"
date: 2018-10-31
forum: Hardware
---

### Post by alexds9 on 2018-10-31
I have a problem with my "SteelSeries Stratus XL" gamepad: the "back" and "guide\home" buttons are not working together with other buttons in games (ubuntu/wine). I know that back\guide buttons are fine because they are working in chrome and other programs. The strange part is that the gamepad appears as 4 different events in "/dev/input/". I tested them with evtest, two events do not respond to any button/joystick. Another event with "back" and "guide" buttons listed as keyboard and working. And the last event contains all the other buttons/joysticks, working fine.


```
$ sudo evtest /dev/input/event27
Input driver version is 1.0.1
Input device ID: bus 0x5 vendor 0x111 product 0x1419 version 0x109
Input device name: "SteelSeries Stratus XL Keyboard"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 139 (KEY_MENU)
    Event code 158 (KEY_BACK)
    Event code 172 (KEY_HOMEPAGE)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
Properties:
Testing ... (interrupt to exit)

```
```
$ sudo evtest /dev/input/event29
Input driver version is 1.0.1
Input device ID: bus 0x5 vendor 0x111 product 0x1419 version 0x109
Input device name: "SteelSeries Stratus XL"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 304 (BTN_SOUTH)
    Event code 305 (BTN_EAST)
    Event code 306 (BTN_C)
    Event code 307 (BTN_NORTH)
    Event code 308 (BTN_WEST)
    Event code 309 (BTN_Z)
    Event code 310 (BTN_TL)
    Event code 311 (BTN_TR)
    Event code 312 (BTN_TL2)
    Event code 313 (BTN_TR2)
    Event code 314 (BTN_SELECT)
    Event code 315 (BTN_START)
    Event code 316 (BTN_MODE)
    Event code 317 (BTN_THUMBL)
    Event code 318 (BTN_THUMBR)
    Event code 319 (?)
  Event type 3 (EV_ABS)
    Event code 0 (ABS_X)
      Value      0
      Min    -2047
      Max     2047
      Flat     255
    Event code 1 (ABS_Y)
      Value      0
      Min    -2047
      Max     2047
      Flat     255
    Event code 2 (ABS_Z)
      Value      0
      Min    -2047
      Max     2047
      Fuzz      15
      Flat     255
    Event code 5 (ABS_RZ)
      Value      0
      Min    -2047
      Max     2047
      Fuzz      15
      Flat     255
      Resolution     745
    Event code 9 (ABS_GAS)
      Value      0
      Min        0
      Max     4095
      Fuzz      15
      Flat     255
    Event code 10 (ABS_BRAKE)
      Value     76
      Min        0
      Max     4095
      Fuzz      15
      Flat     255
    Event code 16 (ABS_HAT0X)
      Value      0
      Min       -1
      Max        1
    Event code 17 (ABS_HAT0Y)
      Value      0
      Min       -1
      Max        1
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 17 (EV_LED)
    Event code 0 (LED_NUML) state 0
    Event code 1 (LED_CAPSL) state 0
    Event code 2 (LED_SCROLLL) state 0
    Event code 3 (LED_COMPOSE) state 0
Properties:
Testing ... (interrupt to exit)

```


I'm not sure how to make "back" and "guide" buttons to work together with the gamepad.
Shouldn't the 4 events be just one?
Maybe I should configure the gamepad in xorg configuration file somehow or do something else?


Gamepad: SteelSeries Stratus XL.
Model #: GC-00002
Firmware: 1.69.0.0

System:
Ubuntu 18.10.
4.18.0-10-generic #11-Ubuntu SMP Thu Oct 11 15:13:55 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by alexds9 on 2018-11-04
Additional information:
When tested in Ubuntu 18.04.1 (4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64) there is a single event for the gamepad, with all the buttons/joysticks registered correctly. Any suggestions what has been changed and how to fix the problem in Ubuntu 18.10?

---

### Post by cmcasanova on 2019-07-28
> **alexds9 said:**
> Additional information:
When tested in Ubuntu 18.04.1 (4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64) there is a single event for the gamepad, with all the buttons/joysticks registered correctly. Any suggestions what has been changed and how to fix the problem in Ubuntu 18.10?

Did you ever figure this out or find a workaround?  I am running 18.04.2 and I am running into the exact same issue as you.

---


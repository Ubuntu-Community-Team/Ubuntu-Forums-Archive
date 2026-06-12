---
title: "Help with sdl2 gamepad"
date: 2016-12-18
forum: Hardware
---

### Post by ulao3 on 2016-12-18
Hello all, I have a gamepad that is compatible with jstest (linuxraw?) and in windows it works with sdl2 and dinput. I'm trying to get it to work in linux with sdl2-jstest. sdl2-jstest is reporting that it can not find any joysticks. I was wondering how you would figure out the snag?

sdl (1.3?)  is ok sdl2 is not

sudo sdl-jstest --list
Found 2 joystick(s)

Joystick Name:     'GPIO Controller 1'
Joystick Number:    0
Number of Axes:     2
Number of Buttons:  8
Number of Hats:     0
Number of Balls:    0

Joystick Name:     'BLISS-BOX 4PLAY PORT' <-----------------this one is the gamepad I'm using.
Joystick Number:    1
Number of Axes:     8
Number of Buttons: 28
Number of Hats:     1
Number of Balls:    1

sdl2-jstest -l
Found 1 joystick(s)

Joystick Name:     'GPIO Controller 1'
Joystick GUID:     15000000010000000100000000010000
Joystick Number:    0
Number of Axes:     2
Number of Buttons:  8
Number of Hats:     0
Number of Balls:    0
GameController:
  not a gamepad




It is a dual device and shows as js0 ms1 and event0. All of this works when using the controller with dolphin(an app using linuxraw I think) but I have an application I need to use with sdl2. Is there something I can do in the OS to determine why it is not listed under sdl(2) apps?

Also I tried to 666 my eventX for a test. I read sdl2 does not use jsX and works off of event's (often with permission issues) but no luck

---

### Post by ulao3 on 2016-12-18
the problem was that dsl2 can not use the device because its a dual device. (mouse joystick) when I rebuild the firmware for the device to be a joystick only, it works). :(

Seems udev does the same thing. No issue in windows with dual device however. Also does libsdl2-2.0 mean the 2.0.0? Because dsl2 is at 2.0.5 and there could have been a fix in 2.0.5.

---


---
title: "I can't use my multitouch screen"
date: 2011-01-16
forum: Hardware
---

### Post by lapoule54 on 2011-01-16
Hello all,

I bought an AOC screen and I'm runing under ubunut 10.10.

the lsinput command give this to me :
/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x408
   product : 0x3001
   version : 272
   name    : "QUANTA Optical Touch Screen"
   phys    : "usb-0000:00:12.2-2.2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

I know this screen should be compatible with 2 fingers points.

I did the gesture testing procedure :
[https://wiki.ubuntu.com/Multitouch/Testing/UsingGesturetest](https://wiki.ubuntu.com/Multitouch/Testing/UsingGesturetest)

and the result is good :(this is en example)

Gesture ID:        55
    Gesture Type:    3: Drag - Two Fingers
    Device ID:    9
    Timestamp:    2279568
    Root Window:    0xb9: (root window)
    Event Window:    0x4000004: "denis@denis-System-Product-Name: ~"
    Child Window:    0x4000004: "denis@denis-System-Product-Name: ~"
    Focus X:    0.000000
    Focus Y:    0.000000
    Status:        2
    Num Props:    16


But now, how can I programme my gesture to stop use my mouse???
How can I ask linux to zoom if I open my finger?
All I have is one finger detection in my day to day application...

please help me.

thank you all.

Denis

---


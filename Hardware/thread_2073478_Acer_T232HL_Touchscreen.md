---
title: "Acer T232HL Touchscreen"
date: 2012-10-19
forum: Hardware
---

### Post by cheeves on 2012-10-19
Hello, 

 I am having a problem with the new Acer T232HL tocuh screen monitor. I am hoping someone could possibly shed some light on what I may be missing. 

 A little background: I am using a NetTop and touchscreen monitors in a kiosk type set up using Ubuntu 10.04LTS. All was working well with the Acer T231H monitor until they discontinued the monitor and I can no longer source any. 

 I bought the new T232HL for testing as a replacement and I was hopeful due to it being a newer version of the T231H. Anyway....

 I have a problem in which the Touch is registering, however the pointer does not move when you touch the screen. If I plug in a USB mouse and move the pointer with the mouse to the area I want to activate (like an launcher on the desktop) with touch, and then touch the screen once the mouse pointer is over the launcher, it will register the touch and launch the selected program. If I unplug the mouse from the USB, the touch will register where ever the pointer is on the screen. 

 I do know that Acer appears to be using a different screen manufacturer for the T232HL as opposed to the T231H (Quanta Computer, Inc). I gleaned this information from lsusb and xinput on the T232HL:

lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 004 Device 003: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 004 Device 002: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2149:2306  
**Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

xinput list:
Virtual core pointer                        id=2    [master pointer  (3)]
âŽœ   â†³ Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
âŽœ   â†³ Logitech Optical USB Mouse                  id=11    [slave  pointer  (2)]
**âŽœ   â†³ Advanced Silicon S.A CoolTouch(TM) System    id=12    [slave  pointer  (2)]**
âŽ£ Virtual core keyboard                       id=3    [master keyboard (2)]
    â†³ Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    â†³ Power Button                                id=6    [slave  keyboard (3)]
    â†³ Power Button                                id=7    [slave  keyboard (3)]
    â†³ Sleep Button                                id=8    [slave  keyboard (3)]
    â†³ Dell Dell USB Keyboard Hub                  id=9    [slave  keyboard (3)]
    â†³ Dell Dell USB Keyboard Hub                  id=10    [slave  keyboard (3)]
    â†³ AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

xinput list-props 12:
Device 'Advanced Silicon S.A CoolTouch(TM) System':
    Device Enabled (115):    1
    Device Accel Profile (232):    0
    Device Accel Constant Deceleration (233):    1.000000
    Device Accel Adaptive Deceleration (235):    1.000000
    Device Accel Velocity Scaling (236):    10.000000
    Evdev Reopen Attempts (230):    10
    Evdev Axis Inversion (237):    0, 0
    Evdev Axis Calibration (238):    <no items>
    Evdev Axes Swap (239):    0
    Axis Labels (240):    "Abs X" (251), "Abs Y" (252), "Abs Z" (253), "Abs Rotary X" (254), "Abs Rotary Y" (255), "Abs Rotary Z" (256), "Abs Throttle" (257), "Abs Rudder" (258), "Abs Wheel" (259), "Abs Gas" (260), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Button Labels (242):    "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241), "Button Wheel Up" (119), "Button Wheel Down" (120)
    Evdev Middle Button Emulation (243):    2
    Evdev Middle Button Timeout (244):    50
    Evdev Wheel Emulation (245):    0
    Evdev Wheel Emulation Axes (246):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (247):    10
    Evdev Wheel Emulation Timeout (248):    200
    Evdev Wheel Emulation Button (249):    4
    Evdev Drag Lock Buttons (250):    0

If anyone has any other insight or suggestions, I would greatly appreciate any and all assistance. Thank you!

---

### Post by cheeves on 2012-10-22
anyone?

---

### Post by wolfies97 on 2012-12-09
Did you find a solution? did you try Ubunu 12.10 with the screen?

---

### Post by cheeves on 2012-12-10
Actually, yes I have found a solution to this. 

I did try 12.10 without much success. Granted I did not spend much time diagnosing Ubuntu 12.10 as the application I am using the touchscreens for is running on 10.04LTS, and the need was there to get it working on the existing installation. 

At any rate, I will post the links for anyone who may stumble upon this with the same problem with this screen. After much digging around google and the forums I ran into this link [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)

After compiling and installing, I still had the issue of the screen not responding to touch until I added support for the device from user space. This is the last bit on the linked page. After this, it works like a champ.

---


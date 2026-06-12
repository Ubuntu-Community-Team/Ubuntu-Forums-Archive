---
title: "Gamepad working partially"
date: 2013-07-06
forum: Hardware
---

### Post by Henne91 on 2013-07-06
Hey everybody!

So, I am trying to set up my Speedlink SL-6534 Gamepad in Ubuntu which is actually:
```
Bus 002 Device 003: ID 0079:0006 DragonRise Inc. Generic USB Joystick
```

according to lsusb which is pretty common hardware.

Now the point is, basic functionality is working. It has 10 buttons, and you can also use the directional pads (is this the right word for those thinggys you use to control where you are going?) to click.

There is two different kinds of d-pads. One is like a big round button and has no clicking functionality and two are like sticks that stand up a bit. The first one is completely working. The other two, however, only work in one direction. The means I can only use the left pad to go left and right while the right one only goes up and down.

I already tried to remap buttons using js or xorg.conf both without success. I used the following xorg.conf from the website systemausfall:
```
Section "InputDevice"
        Identifier      "joystick"
        Driver          "joystick"
        # proper path to your joypad could be found by looking into '/dev/input/by-id' directory
        Option "Device"         "/dev/input/js1"
        # keyboard controls for Axis: http://www.linuxcnc.org/docs/2.4/html/gui_axis.html#r1_4
        # keycodes: "xmodmap -pke"
        # choose axis X (x)
        Option "MapButton1"     "key=53"
        # choose axis Y (y)
        Option "MapButton2"     "key=29"
        # choose axis Z (z)
        Option "MapButton3"     "key=52"
        # axis "zero G54 offset on selected axis" (END)
        Option "MapButton4"     "key=103"
        # axis +Z
        Option "MapButton5"     "key=99"
        # increase jogging speed (comma)
        Option "MapButton6"     "key=60"
        # axis -Z
        Option "MapButton7"     "key=105"
        # reduce jogging speed (period)
        Option "MapButton8"     "key=59"
        # axis "pause program" (p)
        Option "MapButton9"     "key=33"
        # axis "continus program" (s)
        Option "MapButton10"    "key=39"
        # mouse button: left
        Option "MapButton11"    "button=1"
        # mouse button: right
        Option "MapButton12"    "button=3"
        # axis X - Left /Right
        Option "MapAxis1"       "mode=relative deadzone=28000 keylow=100 keyhigh=102 axis=0.15key"
        # axis Y - Up / Down
        Option "MapAxis2"       "mode=relative deadzone=28000 keylow=98 keyhigh=104 axis=0.15key"
        # same as Axis1 - should be ignored
        Option "MapAxis3"       "mode=none"
        # Mouse (horizontal)
        Option "MapAxis4"       "mode=relative deadzone=2000 axis=+0.5x"
        # Mouse (vertical)
        Option "MapAxis5"       "mode=relative deadzone=2000 axis=+0.5y"
        # Homing (HOME) / jogging control continous mode (c)
        Option "MapAxis6"       "mode=accelerated deadzone=10000 keylow=97 keyhigh=54"
        # change jogging step (i / I)
        Option "MapAxis7"       "mode=accelerated deadzone=10000 keylow=31 keyhigh=50,31"
EndSection

Section "ServerLayout"
        Identifier      "DefaultServerLayout"
        InputDevice     "Joystick"      "SendCoreEvents"
EndSection

Section "ServerFlags"
        # This is an ugly way to disable the mouse pointer ability of the
        # gamepad. Otherwise the gamepad is interpreted as a mouse _and_
        # as a keyboard input (as defined above).
        Option "AutoAddDevices" "False"
EndSection
```

But if I enable this I am not able to use my mouse and keyboard anymore although in says in the last section, that the option there should prevent this.

Another problem is that I cannot switch from Digital to Analog and vice versa. When I press the button for this the LED on the gamepad doesn't turn on.

Also my gamepad supports force feedback. Google told me there is a kernel module for my gamepad to enable ff support but I only found how to set this up in Gentoo by compiling your own kernel. I really don't want to do that. Isn't there an easier way? Tried to test with fftest, but it says 

```
Device /dev/input/js1 opened
Ioctl query: Invalid argument
```

I am using the officially supported raring kernel (3.8) for Ubuntu 12.04.2 LTS by the way.

Any ideas?

Thanks!
Hendrik

---


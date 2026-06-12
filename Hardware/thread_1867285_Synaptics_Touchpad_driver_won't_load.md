---
title: "Synaptics Touchpad driver won't load"
date: 2011-10-22
forum: Hardware
---

### Post by Bocete on 2011-10-22
Hi,

I'm a new member, new to Linux as well. I love it so far.

Introduction: I've installed Kubuntu 11.10 on my new Asus G74 laptop, and everything seems to be alright except I have some touchpad issues: after I move the cursor, occasionally it will click by it's own after a few seconds. This is really annoying, clicking on a textfield to type in it only to have the caret jump back and stuff like that.

I hope it's not that silly Kubuntu KMouse utility going wild (it's a tool that will click for you when you stop moving the cursor, to keep you safe from carpal tunnel and what-not). I think it's not because when I turn that utility on it works as expected; when I turn it off I see that random mouse click trigger only occasionally, usually when I start typing.

Anyway, I'll head over to the Kubuntu forums to see if there are any other "helpful" utilities ruining my experience, or if there is anything else I could do.

The issue I want to discuss here: my Synaptics driver doesn't load. And yes, I've searched high and low for the solution in the past week.

While trying to see if the touchpad is causing those random triggers, I've found that I don't have the Touchpad tab under Mouse settings. That is, I have it, but it contains a message "no touchpad was detected on your system. Please make sure that the synaptics driver is properly installed and configured". My touchpad works properly, so the system is using some random driver at this moment.

 I think I've narrowed the problem to my /usr/share/X11/xorg.conf.d/50-synaptics.conf file not being used at all.

Excerpt from /var/log/Xorg.0.log:
```

...
[    22.435] (II) config/udev: Adding input device FSPPS/2 Sentelic FingerSensingPad (/dev/input/event9)
[    22.435] (**) FSPPS/2 Sentelic FingerSensingPad: Applying InputClass "evdev pointer catchall"
[    22.435] (II) Using input driver 'evdev' for 'FSPPS/2 Sentelic FingerSensingPad'
[    22.435] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.435] (**) FSPPS/2 Sentelic FingerSensingPad: always reports core events
[    22.435] (**) FSPPS/2 Sentelic FingerSensingPad: Device: "/dev/input/event9"
[    22.435] (--) FSPPS/2 Sentelic FingerSensingPad: Found 11 mouse buttons
[    22.435] (--) FSPPS/2 Sentelic FingerSensingPad: Found scroll wheel(s)
[    22.435] (--) FSPPS/2 Sentelic FingerSensingPad: Found relative axes
[    22.435] (--) FSPPS/2 Sentelic FingerSensingPad: Found x and y relative axes
[    22.435] (II) FSPPS/2 Sentelic FingerSensingPad: Configuring as mouse
[    22.435] (II) FSPPS/2 Sentelic FingerSensingPad: Adding scrollwheel support
[    22.435] (**) FSPPS/2 Sentelic FingerSensingPad: YAxisMapping: buttons 4 and 5
[    22.435] (**) FSPPS/2 Sentelic FingerSensingPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.436] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input9/event9"
[    22.436] (II) XINPUT: Adding extended input device "FSPPS/2 Sentelic FingerSensingPad" (type: MOUSE)
[    22.436] (II) FSPPS/2 Sentelic FingerSensingPad: initialized for relative axes.
[    22.436] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) keeping acceleration scheme 1
[    22.436] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) acceleration profile 0
[    22.436] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) acceleration factor: 2.000
[    22.436] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) acceleration threshold: 4
[    22.436] (II) config/udev: Adding input device FSPPS/2 Sentelic FingerSensingPad (/dev/input/mouse0)
[    22.436] (II) No input driver/identifier specified (ignoring)
...

```When calling "synclient" over terminal, I get a message
```
Couldn't find synaptics properties. No synaptics driver loaded?
```xinput list:
```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; FSPPS/2 Sentelic FingerSensingPad         id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]

```/usr/share/X11/xorg.conf.d/10-evdev.conf
```

#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

```/usr/share/X11/xorg.conf.d/50-synaptics.conf
```

# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
EndSection

```

lshw doesn't mention my touchpad at all, but neither my USB mouse when I plug it in, nor the keyboard. I'm guessing lshw shouldn't list them, but I don't know, new to Linux.

So I'm thinking that the 50-synaptics file is not being used at all. If you look at the Xorg log, you'll see that after the input0 device has been added no drivers have been found that match it's description. Maybe that description does not contain "touchpad" in it? Humph. I have absolutely no idea on how to "force" a driver on a input device.

I have the latest xserver-xorg-input-synaptic package, of course. I haven't done any configuration on it since I'm not sure on how to do that, or even if I need to do it.

What should be my next step?

Thanks,
Bo

---

### Post by corevalue on 2012-01-04
I have a MSICR720 laptop, Kubuntu 11.10 and updated, and the output of the /var/log/xorg.0.log reports the same Sentelic fingerpad. I also have the problem of random cursor movements when typing. The touchpad works, is reported in the log, but is shown as not detected under system settings.

By playing with synaptics, i have managed to get an error message at startup, "No touchpad on this system", when there plainly is, and it works.

[    21.567] (II) config/udev: Adding input device FSPPS/2 Sentelic FingerSensingPad (/dev/input/event10)
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: Applying InputClass "evdev pointer catchall"
[    21.567] (II) Using input driver 'evdev' for 'FSPPS/2 Sentelic FingerSensingPad'
[    21.567] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: always reports core events
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: Device: "/dev/input/event10"
[    21.567] (--) FSPPS/2 Sentelic FingerSensingPad: Found 11 mouse buttons
[    21.567] (--) FSPPS/2 Sentelic FingerSensingPad: Found scroll wheel(s)
[    21.567] (--) FSPPS/2 Sentelic FingerSensingPad: Found relative axes
[    21.567] (--) FSPPS/2 Sentelic FingerSensingPad: Found x and y relative axes
[    21.567] (II) FSPPS/2 Sentelic FingerSensingPad: Configuring as mouse
[    21.567] (II) FSPPS/2 Sentelic FingerSensingPad: Adding scrollwheel support
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: YAxisMapping: buttons 4 and 5
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.567] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    21.567] (II) XINPUT: Adding extended input device "FSPPS/2 Sentelic FingerSensingPad" (type: MOUSE)
[    21.567] (II) FSPPS/2 Sentelic FingerSensingPad: initialized for relative axes.
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) keeping acceleration scheme 1
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) acceleration profile 0
[    21.567] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) acceleration factor: 2.000
[    21.568] (**) FSPPS/2 Sentelic FingerSensingPad: (accel) acceleration threshold: 4
[    21.568] (II) config/udev: Adding input device FSPPS/2 Sentelic FingerSensingPad (/dev/input/mouse1)
[    21.568] (II) No input driver/identifier specified (ignoring)
[    38.146] (II) XKB: reuse xkmfile /var/lib/xkb/server-5550814D3DE81657FB75A6E398FC443242E652DD.xkm
[    43.576] (II) intel(0): EDID vendor "AUO", prod id 4254
[    43.576] (II) intel(0): Printing DDC gathered Modelines:
[    43.576] (II) intel(0): Modeline "1600x900"x0.0  110.40  1600 1664 1706 2000  900 903 906 920 -hsync -vsync (55.2 kHz)

---

### Post by Bocete on 2012-01-04
Hi,
 
I pretty much gave up on this. I've come to realize that Kubuntu assumes the Touchpad is just another mouse and have left at that.

As for the sporadic clicking/moving, to my shame, I've been touching the touchpad with my left hand. It's huge on a G74, not recessed and, on Linux (again because of drivers), as sensitive as they come. I don't even have to apply any pressure, any minimal surface contact; it's just like that.

Not helpful, but that's the update.

- Bo

---


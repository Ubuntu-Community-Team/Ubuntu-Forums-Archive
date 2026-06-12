---
title: "udev rules and ConstantDeceleration"
date: 2010-05-28
forum: Hardware
---

### Post by aziztcf on 2010-05-28
Hey, I'm trying to write udev rule which sets the Constant Deceleration according to which mouse I plug in. However the ENV{x11_options.ConstantDeceleration} doesn't seem to work? 

 Then I tried making it change the deceleration by runnin xinput set-prop, but it doesn't work either(udevadm test gives util_run_program: '/usr/bin/xinput' (stderr) 'Unable to connect to X server') This is the method I use when I set the value manually.

First time screwing around with the udev, and man it's awesome. Sure I could have two shortcuts for changing the sensitivity but where's the fun in that?!

Any ideas?

E: Wait, so as of 10.04 it's now done in xorg.conf.d? God damn it.

E2: Made 10-sensitivity.conf in /usr/lib/X11/xorg.conf.d/

> Section "InputClass"
    Identifier "Razer sensitivity"
    MatchIsPointer "on"
    MatchProduct "Razer Razer Diamondback Optical Mouse"
    Option "ConstantDeceleration" "5"

EndSectionIt runs... > (II) config/udev: Adding input device Razer Razer Diamondback Optical Mouse (/dev/input/event5)
(**) Razer Razer Diamondback Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Razer Razer Diamondback Optical Mouse: Applying InputClass "Razer sensitivity"
(**) Razer Razer Diamondback Optical Mouse: always reports core events
(**) Razer Razer Diamondback Optical Mouse: Device: "/dev/input/event5"
(II) Razer Razer Diamondback Optical Mouse: Found 11 mouse buttons
(II) Razer Razer Diamondback Optical Mouse: Found scroll wheel(s)
(II) Razer Razer Diamondback Optical Mouse: Found relative axes
(II) Razer Razer Diamondback Optical Mouse: Found x and y relative axes
(II) Razer Razer Diamondback Optical Mouse: Configuring as mouse
(**) Razer Razer Diamondback Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Razer Razer Diamondback Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Razer Razer Diamondback Optical Mouse" (type: MOUSE)
(II) Razer Razer Diamondback Optical Mouse: initialized for relative axes.But doesn't change the deceleration value.

Whoops, apparently there's a thread about this already,[http://ubuntuforums.org/showthread.php?t=1469566](http://ubuntuforums.org/showthread.php?t=1469566) , merge please.

Updated from xorg-edgers ppa to 2:1.8.1+git20100521 , now the xorg.conf.d rules seem to work.

---

### Post by Sciesch on 2010-06-25
I've found that the Deceleration-settings did not take effect, until I moved the sliders in Preferences / Mouse up from zero. Then suddenly my mouse was slow as hell and I could adjust the values properly in the terminal.

I now have it set to:
xinput --set-prop "Razer Razer Diamondback 3G" "Device Accel Constant Deceleration" 2.5

---


---
title: "Touching graphics tablet with pen crashes X"
date: 2011-08-02
forum: Hardware
---

### Post by lkm32 on 2011-08-02
Well, I bought this monoprice graphics tablet a month or two ago and it was working fine with the wizardpen drivers ... however, recently it has started to crash the X server whenever I attempt to use it (tried all kinds of plugging in and out).

Here is the device from lsusb:
```
Bus 002 Device 005: ID 5543:0064 UC-Logic Technology Corp. Aiptek HyperPen 10000U
```and here is a bit of the Xorg.0.log that I hope might be useful:
```

[    77.380] (II) No input driver/identifier specified (ignoring)
[    77.381] (II) config/udev: Adding input device UC-LOGIC TWA60 (/dev/input/event5)
[    77.381] (**) UC-LOGIC TWA60: Applying InputClass "evdev pointer catchall"
[    77.381] (**) UC-LOGIC TWA60: Applying InputClass "evdev tablet catchall"
[    77.381] (II) Using input driver 'evdev' for 'UC-LOGIC TWA60'
[    77.381] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.381] (**) UC-LOGIC TWA60: always reports core events
[    77.381] (**) UC-LOGIC TWA60: Device: "/dev/input/event5"
[    77.381] (--) UC-LOGIC TWA60: Found 10 mouse buttons
[    77.381] (--) UC-LOGIC TWA60: Found scroll wheel(s)
[    77.381] (--) UC-LOGIC TWA60: Found relative axes
[    77.381] (--) UC-LOGIC TWA60: Found x and y relative axes
[    77.381] (--) UC-LOGIC TWA60: Found absolute axes
[    77.381] (II) evdev-grail: failed to open grail, no gesture support
[    77.381] (--) UC-LOGIC TWA60: Found x and y absolute axes
[    77.381] (--) UC-LOGIC TWA60: Found absolute tablet.
[    77.381] (II) UC-LOGIC TWA60: Configuring as tablet
[    77.381] (II) UC-LOGIC TWA60: Adding scrollwheel support
[    77.381] (**) UC-LOGIC TWA60: YAxisMapping: buttons 4 and 5
[    77.381] (**) UC-LOGIC TWA60: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    77.381] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input5/event5"
[    77.381] (II) XINPUT: Adding extended input device "UC-LOGIC TWA60" (type: TABLET)
[    77.381] (WW) UC-LOGIC TWA60: touchpads, tablets and touchscreens ignore relative axes.
[    77.381] (II) UC-LOGIC TWA60: initialized for absolute axes.
[    77.381] (**) UC-LOGIC TWA60: (accel) keeping acceleration scheme 1
[    77.381] (**) UC-LOGIC TWA60: (accel) acceleration profile 0
[    77.381] (**) UC-LOGIC TWA60: (accel) acceleration factor: 2.000
[    77.381] (**) UC-LOGIC TWA60: (accel) acceleration threshold: 4
[    77.382] (II) config/udev: Adding input device UC-LOGIC TWA60 (/dev/input/mouse2)
```If you need any more information I will be more than happy to oblige :D

Thank You all in advance :smile:

---

### Post by Favux on 2011-08-02
Hi lkm32,

That lsusb is a little confusing but I'm fairly sure it's a UC-LOGIC and so you're right it uses the Wizardpen X driver and not the Aiptek X driver.

Right now your Xorg.0.log shows the tablet is on the evdev X driver.  So you probably want to reinstall the Wizardpen driver.  My guess is at least the 70-wizardpen.conf is missing from /usr/share/X11/xorg.conf.d for whatever reason.

You might also want to check out this thread:  [http://ubuntuforums.org/showthread.php?t=1645019](http://ubuntuforums.org/showthread.php?t=1645019)

---

### Post by lkm32 on 2011-08-03
> **Favux said:**
> Hi lkm32,

That lsusb is a little confusing but I'm fairly sure it's a UC-LOGIC and so you're right it uses the Wizardpen X driver and not the Aiptek X driver.

Right now your Xorg.0.log shows the tablet is on the evdev X driver.  So you probably want to reinstall the Wizardpen driver.  My guess is at least the 70-wizardpen.conf is missing from /usr/share/X11/xorg.conf.d for whatever reason.

You might also want to check out this thread:  [http://ubuntuforums.org/showthread.php?t=1645019](http://ubuntuforums.org/showthread.php?t=1645019)

Oddly enough, that is the same thread that I used to set this tablet up (kudos then); however my problem seems to be that ANY activity on behalf of the tablet/pen (even just getting it close) crashes the X-server and puts me back on the log-in screen ](*,)

here is my output from "xinput --list" :
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)    id=8    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWA60                              id=9    [slave  pointer  (2)]
&#9116;   &#8627; BTC USB Multimedia Cordless Kit             id=11    [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; BTC USB Multimedia Cordless Kit             id=10    [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                   id=12    [slave  keyboard (3)]
```and the updated Xorg.0.log output for the tablet:
```
[   597.904] (II) No input driver/identifier specified (ignoring)
[   597.904] (II) config/udev: Adding input device UC-LOGIC TWA60 (/dev/input/event5)
[   597.904] (**) UC-LOGIC TWA60: Applying InputClass "evdev pointer catchall"
[   597.904] (**) UC-LOGIC TWA60: Applying InputClass "evdev tablet catchall"
[   597.904] (II) Using input driver 'evdev' for 'UC-LOGIC TWA60'
[   597.904] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   597.904] (**) UC-LOGIC TWA60: always reports core events
[   597.904] (**) UC-LOGIC TWA60: Device: "/dev/input/event5"
[   597.904] (--) UC-LOGIC TWA60: Found 10 mouse buttons
[   597.904] (--) UC-LOGIC TWA60: Found scroll wheel(s)
[   597.904] (--) UC-LOGIC TWA60: Found relative axes
[   597.904] (--) UC-LOGIC TWA60: Found x and y relative axes
[   597.904] (--) UC-LOGIC TWA60: Found absolute axes
[   597.905] (II) evdev-grail: failed to open grail, no gesture support
[   597.905] (--) UC-LOGIC TWA60: Found x and y absolute axes
[   597.905] (--) UC-LOGIC TWA60: Found absolute tablet.
[   597.905] (II) UC-LOGIC TWA60: Configuring as tablet
[   597.905] (II) UC-LOGIC TWA60: Adding scrollwheel support
[   597.905] (**) UC-LOGIC TWA60: YAxisMapping: buttons 4 and 5
[   597.905] (**) UC-LOGIC TWA60: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   597.905] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input5/event5"
[   597.905] (II) XINPUT: Adding extended input device "UC-LOGIC TWA60" (type: TABLET)
[   597.905] (WW) UC-LOGIC TWA60: touchpads, tablets and touchscreens ignore relative axes.
[   597.905] (II) UC-LOGIC TWA60: initialized for absolute axes.
[   597.905] (**) UC-LOGIC TWA60: (accel) keeping acceleration scheme 1
[   597.905] (**) UC-LOGIC TWA60: (accel) acceleration profile 0
[   597.905] (**) UC-LOGIC TWA60: (accel) acceleration factor: 2.000
[   597.905] (**) UC-LOGIC TWA60: (accel) acceleration threshold: 4
[   597.905] (II) config/udev: Adding input device UC-LOGIC TWA60 (/dev/input/mouse2)
[   597.905] (**) UC-LOGIC TWA60: Ignoring device from InputClass "WizardPen ignore mouse dev class"
```And finally here is my /usr/share/X11/xorg.conf.d/70-wizardpen.conf:
```
Section "InputClass"
Identifier "WizardPen class"
MatchIsTablet "on"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_TWA60-event-mouse"
Driver "wizardpen"
Option "TopX" "93"
Option "TopY" "701"
Option "BottomX" "19936"
Option "BottomY" "13165"
EndSection

Section "InputClass"
Identifier "WizardPen ignore mouse dev class"
MatchIsTablet "on"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
MatchDevicePath "/dev/input/mouse*"
Option "Ignore" "yes"
EndSection
```I don't know why X would crash as there is no indication in the log (I will attach it just in case though).

As it is right now, if I purge the wizardpen packages X will not crash upon a touch ... however, the tablet also has no effect at all on the cursor (no movement at all).

Tried the Aiptek drivers since I'm kinda desperate (didn't work ... same crashing problem).

Any ideas? I would be glad to post any information that is needed. :)

Again, thank you very much.

---

### Post by Favux on 2011-08-03
I think the:
> Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
at the end of the Xorg.0.log is from the Nvidia driver.  We need to wonder if that is involved in X crashing.

First try changing:
```
MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_TWA60-event-mouse"

```
to
```
    MatchDevicePath "/dev/input/event*"

```
Out of curiosity what does *ls /dev/input/by-id* show anyway?

If that doesn't do anything could you maybe try uninstalling the *Mouseemu virtual mouse* and see if the WizardPen driver still crashes X?  And you might want to consider also trying that with the *BTC USB Multimedia Cordless Kit* if Mouseemu removal doesn't help.

---

### Post by lkm32 on 2011-08-04
It worked!
I purged the "mouseemu" package and it started working again! :D

Thank You for your amazing help!  
I will mark this thread as solved ... providing I find a way how to.:confused: (EDIT: found it!)

Again, thank you! \\:D/
PS. what do you think the mouseemu package had to do with it?

Cheerios

---

### Post by Favux on 2011-08-04
Great!  :)

I think it is grabbing/monopolizing the pointer X inputs and not working correctly with the ones from the WizardPen driver.

---


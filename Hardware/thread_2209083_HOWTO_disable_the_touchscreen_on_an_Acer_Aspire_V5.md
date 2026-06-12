---
title: "HOWTO: disable the touchscreen on an Acer Aspire V5-122P (0889)"
date: 2014-03-03
forum: Hardware
---

### Post by Cinderboot on 2014-03-03
Hi all,
I have been very happy with this sleekbook, but the touchscreen is useless to me, plus I hate fingerprints. Also, I would occasionally get weird characters in the terminal (^A, P, +,.. I don't exactly remember which) that I'm guessing was coming from the touchscreen.

$ xinput --list 

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                             id=11   [slave  pointer  (2)]
&#9116; &#8627; ELAN Touchscreen id=12 [slave pointer (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                  id=14   [slave  pointer  (2)]
&#9116;   &#8627; Ultrathin Touch Mouse                     id=16   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; HID 0a5c:4502                             id=10   [slave  keyboard (3)]
    &#8627; HD WebCam                                 id=16 [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                          id=15   [slave  keyboard (3)]


And of course I tried:

$ xinput set-prop 12 'Device Enabled' 0

But as soon as I touch the screen it enables again...  so, the best (permanent) solution I could find was to edit /usr/share/X11/xorg.conf.d/10-evdev.conf

>> Add Option "Ignore" "on" to the touchscreen section so it looks like this:

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "Ignore" "on"
EndSection

Enjoy!

---


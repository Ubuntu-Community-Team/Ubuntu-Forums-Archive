---
title: "Disable touchscreen on x1 carbon when closed"
date: 2016-10-19
forum: Hardware
---

### Post by jeromecovington on 2016-10-19
I like to use my x1 carbon with the lid closed, and plugged into an external monitor. The problem is, the touchscreen misbehaves, causing weird tracking issues with the usb mouse (the cursor jumps about).

I edited  /usr/share/X11/xorg.conf.d/10-evdev.conf as such:

    Section "InputClass"
            Identifier "evdev touchscreen catchall"
            MatchIsTouchscreen "on"
            MatchDevicePath "/dev/input/event*"
            Driver "evdev"
            Option "Ignore" "on"
    EndSection

That solved my issue when working with the external monitor, but when I used my laptop later without the external monitor, the trackpad wasn't working.

Does anybody know how to disable the touchscreen but keep the trackpad functional?

Here are the entire contents of the file (without the "Ignore" option).

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

Note: I posted this on askubuntu as well, although saw no activity there: [http://askubuntu.com/questions/838783/disable-touchscreen-on-x1-carbon-when-closed](http://askubuntu.com/questions/838783/disable-touchscreen-on-x1-carbon-when-closed)
I'm hoping that the community here may have more ideas.

---

### Post by jeromecovington on 2016-10-19
The following is an _ok_ solution. I would really like to only disable the touchscreen when the laptop is closed, and leave it functional when open. Does anybody have any ideas?

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        # MatchIsTouchscreen "on"
        MatchIsTouchscreen "off"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

---

### Post by jeromecovington on 2016-10-19
Nope, I was wrong, even with the "solution" above, the mouse still jumps around when the lid is closed and using the eternal monitor.

---


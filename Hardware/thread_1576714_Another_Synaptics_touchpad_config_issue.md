---
title: "Another Synaptics touchpad config issue"
date: 2010-09-17
forum: Hardware
---

### Post by tiliqua_au on 2010-09-17
Hi all. First post, as this seems to be first time google can't answer my questions...

I have a synaptics touchpad on an acer aspire netbook running 10.04 UNE.  I set the following config options in /usr/lib/X11/xorg.conf.d/10-synaptics.conf:

```

Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "SHMConfig"  "on"
    Option "RightEdge"  "4500"
    Option "VertTwoFingerScroll" "1"
    Option "TapButton2" "2"
    Option "TapButton3" "3"

EndSection

```However, the only option that "sticks" is "RightEdge". synclient -l shows the following:
```

Parameter settings:
<snip>
    RightEdge               = 4500
    VertTwoFingerScroll     = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
<snip>

```I workaround by adding a script that uses synclient to set the options to the gnome startup applications list, but I'd prefer to set them properly and permanently.

Any suggestions?

---

### Post by tiliqua_au on 2011-01-01
Anybody?

---

### Post by Kalimol on 2011-01-01
Two finger scroll can be set through the GUI and will stick (Preferences>Mouse>Touchpad tab). I think that app is resetting the other bits, though. 

It's highly weird that you have middle-click as the two-finger tap, but I like it. = )

---

### Post by tiliqua_au on 2011-01-01
The 2 finger scroll "preference" sticks when I set it via gpointing-device-settings (ie the option is checked), but it doesn't actually work. synclient shows: 

```
synclient -l |grep VertT
    VertTwoFingerScroll     = 0
```

If I uncheck it and recheck it, then 2 finger scroll works.

Oh and I use 2 finger tap as middle click simply because I use the middle click far more than right click, mainly for opening and closing tabs in my web browser.

---

### Post by tiliqua_au on 2011-07-29
I have *finally* found the answer... 

gnome-settings-daemon hardcodes a few settings that are not exposed in the GUI  (Preferences>Mouse>Touchpad tab/gpointing-device-settings). So  the preferences I set via /usr/share/X11/xorg.conf.d/50-synaptics.conf or /etc/udev/rules.d/66-xorg-synaptics.rules get overwritten.

[https://bbs.archlinux.org/viewtopic.php?id=107398](https://bbs.archlinux.org/viewtopic.php?id=107398)
[https://bugzilla.redhat.com/show_bug.cgi?id=518502](https://bugzilla.redhat.com/show_bug.cgi?id=518502)

The fix is to open gconf-editor and go to /apps/gnome-settings-daemon/plugins/mouse/ and uncheck the active key. Another option is to use a patched g-s-d from [https://launchpad.net/~yurivkhan/+archive/ppa](https://launchpad.net/~yurivkhan/+archive/ppa)

---

### Post by tiliqua_au on 2011-10-18
Update for 11.10.

In dconf-editor, uncheck org/gnome/settings-daemon/plugins/mouse active 
Via command line: ```
gsettings set org.gnome.settings-daemon.plugins.mouse active 'false' 
``` then log out and back in.

---


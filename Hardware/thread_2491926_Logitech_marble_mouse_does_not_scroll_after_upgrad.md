---
title: "Logitech marble mouse does not scroll after upgrade to 22.04"
date: 2023-10-25
forum: Hardware
---

### Post by Richard-S on 2023-10-25
Marble mouse does not scroll in 22.04 upgrade.
I have checked the /usr/share/X11/xorg.conf.d/40-libinput.conf  (and the 10-libinput.conf in that directory). They both contain this:

Section "InputClass"
        Identifier  "Marble Mouse"
        MatchProduct "Logitech USB Trackball"
        Driver "libinput"
        Option "ScrollMethod" "button"
        Option "ScrollButton" "8"
EndSection

which worked fine in 20.04. and is recommended by Ubuntu for all versions after 18.04.

I created a 39-libinput.conf and added the above as suggested in [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

I still can't get it to scroll.
My next step is to re-install 20.04 and stick with that until 
the life-of-service runs out, and then stick to Arch.
I run an Arch machine and the mouse scrolls perfectly in that.

---

### Post by beam-u on 2023-12-12
Hi Richard,

Have had the same problem with the xorg.conf getting seemingly ignored in 22.04

Using gsettings finally solved it for me. Hope this helps you and whoever else finds this as well:

Check your settings with: gsettings list-recursively org.gnome.desktop.peripherals.trackball

Then set: gsettings set org.gnome.desktop.peripherals.trackball middle-click-emulation true
And :       gsettings set org.gnome.desktop.peripherals.trackball scroll-wheel-emulation-button 8

Good luck :)

---

### Post by Richard-S on 2024-01-02
Great! That got the mouse to scroll. Now it is in reverse. What used to be up in 20.04 is now down. But at least the damn thing scrolls.

Richard

---

### Post by orengolan on 2024-10-17
I am on 24.04 and this didn't work for me. Any ideas?


gsettings list-recursively org.gnome.desktop.peripherals.trackball

org.gnome.desktop.peripherals.trackball accel-profile 'default'
org.gnome.desktop.peripherals.trackball middle-click-emulation true
org.gnome.desktop.peripherals.trackball scroll-wheel-emulation-button 8
org.gnome.desktop.peripherals.trackball scroll-wheel-emulation-button-lock false

---

### Post by orengolan on 2024-10-17
I am on 24.04 and this didn't work for me. Any ideas?


gsettings list-recursively org.gnome.desktop.peripherals.trackball

org.gnome.desktop.peripherals.trackball accel-profile 'default'
org.gnome.desktop.peripherals.trackball middle-click-emulation true
org.gnome.desktop.peripherals.trackball scroll-wheel-emulation-button 8
org.gnome.desktop.peripherals.trackball scroll-wheel-emulation-button-lock false

---


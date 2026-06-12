---
title: "sonypi and function key bindings"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by draggett on 2006-02-05
I have successfully installed sonypi and spicctrl on my Vaio PCG-Z1RMP along with Ubuntu 5.10 (breezy) and am able to change the volume with F2-F4 and the display brightness with F5-F6. However, F2 mutes audio while F3 makes it quieter. The graphic on F3 indicates that it is intended for muting audio and not F2. Does anyone know where the key bindings are held?

I previously used sonypi with sonypid, sonykeyd and sonykey.sh (on Mandrake). I was able to define my own key bindings, e.g. to invoke the radeontool utility for enabling/disabling the backlight (my system has the ATI Radeon Mobility chipset). I reckon I could use a script in /etc/rd*/ to launch sonypid and sonykeyd, but would appreciate some advice as to how to do this and whether it would conflict with the default keybinding behavior supported by breezy when the sonypi module is loaded?

---

### Post by scubajeff on 2006-02-06
You need to modify the scripts in /etc/acpi/events. The one mutes audio is "sony-mute", the one makes it quieter is "sony-volume-down".

---


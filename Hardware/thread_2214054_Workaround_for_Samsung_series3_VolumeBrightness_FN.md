---
title: "Workaround for Samsung series3 Volume/Brightness FN control buttons"
date: 2014-03-30
forum: Hardware
---

### Post by tadis on 2014-03-30
Hi all.

So I have Samsung series 3 Laptop (NP350V5C) and it seems that keyboard Volume control buttons does not work at all on ubuntu 13.04 / 13.10 / 14.04.
When I press Fn+VolumeUp or Fn+VolumeDown - volume goes to maximum or minimum, but I cant regulate it.

_Workaround:_

You need to edit file ```
/lib/udev/hwdb.d/60-keyboard.hwdb
```

Find line in SAMSUNG section:

```
# Series 3
keyboard:dmi:bvn*:bvr*:bd*:svn[sS][aA][mM][sS][uU][nN][gG]*:pn*300E[457]*:pvr*
...
```

Add these lines just before # Series 3:

```
# Workaround for samsung 350V 
keyboard:dmi:bvn*:bvr*:bd*:svn[sS][aA][mM][sS][uU][nN][gG]*:pn*350V*:pvr*
 KEYBOARD_KEY_ce=!calc                    # Fn+F1  launch control setting / Run calculator
 KEYBOARD_KEY_d5=!wlan                    # Fn+F12 WiFi On/Off
 KEYBOARD_KEY_89=!brightnessdown          # Fn+F2
 KEYBOARD_KEY_88=!brightnessup            # Fn+F3
 KEYBOARD_KEY_82=!switchvideomode         #Fn+F4
 KEYBOARD_KEY_f7=!f22                     # Unknown (mouse trackpad / PrtSc / ...)
 KEYBOARD_KEY_f9=!f23                     # Unknown (mouse trackpad / PrtSc / ...)
 KEYBOARD_KEY_a0=!mute                    # Fn+F6
 KEYBOARD_KEY_ae=!volumedown              # Fn+F7
 KEYBOARD_KEY_b0=!volumeup                # Fn+F8
 KEYBOARD_KEY_b3=!prog3                   # Unknown (mouse trackpad / PrtSc / ...)

# Series 3
keyboard:dmi:bvn*:bvr*:bd*:svn[sS][aA][mM][sS][uU][nN][gG]*:pn*300E[457]*:pvr*
...
```


Save the file and run this command from terminal as root:

```
# dpkg-reconfigure udev
```

Restart computer.

This workaround will work until next 60-keyboard.hwdb update.


You're welcome! ;)

---


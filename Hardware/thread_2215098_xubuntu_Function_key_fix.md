---
title: "xubuntu: Function key fix"
date: 2014-04-04
forum: Hardware
---

### Post by bungler2 on 2014-04-04
Edit: Apparently there's some kind of conflict between the function keys and the shortcut keys going on, no matter the Language Settings. After a reboot the function key works, after a re-login, the shotcut keys work. They don't work at the same time. Any idea on this are appreciated.

The machine is a Samsung N130. After installing xubuntu, I noticed the the backlight function keys work properly (Fn-Up, Fn-Down), but the the volume controls (Fn-Left, Fn-Right) was not. After searching the web, I found reference to 60-keyboard.hwdb:

```
sudo vim /lib/udev/hwdb.d/60-keyboard.hwdb
```

I searched for "Samsung" and found a list of key codes and bindings:

```
 KEYBOARD_KEY_74=prog1                                  # User key
 KEYBOARD_KEY_75=www
 KEYBOARD_KEY_78=mail
 KEYBOARD_KEY_82=!switchvideomode                       # Fn+F4 CRT/LCD (high keycode: "displaytoggle")
 KEYBOARD_KEY_83=!battery                               # Fn+F2
 KEYBOARD_KEY_84=!prog1                                 # Fn+F5 backlight on/off
 KEYBOARD_KEY_86=!wlan                                  # Fn+F9
 KEYBOARD_KEY_88=!brightnessup                          # Fn+Up
 KEYBOARD_KEY_89=!brightnessdown                        # Fn+Down
 KEYBOARD_KEY_b1=!prog2                                 # Fn+F7 run Samsung Magic Doctor (keypressed event is generated twice)
 KEYBOARD_KEY_b3=!prog3                                 # Fn+F8 switch power mode (battery/dynamic/performance)
 KEYBOARD_KEY_b4=!wlan                                  # Fn+F9 (X60P)
 KEYBOARD_KEY_c5=!prog3                                 # Fn+F8 switch power mode (battery/dynamic/performance)
 KEYBOARD_KEY_d5=!wlan                                  # Fn+F12 wlan/airplane switch
 KEYBOARD_KEY_f7=!f22                                   # Fn+F10 Touchpad on
 KEYBOARD_KEY_f9=!f23                                   # Fn+F10 Touchpad off

```

So, I figured if I found the correct key codes I should be able to map them correctly. Searching again, I found a way to print key codes:

```
xmodmap -pk > mykeyboard.txt
cat mykeyboard.txt | less
```

There I found:

```
     83         0xff96 (KP_Left)        0xffb4 (KP_4)   0xff96 (KP_Left)        0xffb4 (KP_4)
     84         0xff9d (KP_Begin)       0xffb5 (KP_5)   0xff9d (KP_Begin)       0xffb5 (KP_5)
     85         0xff98 (KP_Right)       0xffb6 (KP_6)   0xff98 (KP_Right)       0xffb6 (KP_6)

```
Then I went back into 60-keyboard.hwdb and added the following lines in the appropriate section:

```
 KEYBOARD_KEY_83=!volumedown
 KEYBOARD_KEY_85=!volumeup

```
Saved, exited and ran:

```
sudo udevadm hwdb --update
```


Restarted the machine, but this did nothing! So, I moved on to the next issue (why do we have to clean up 1000 issues after every fresh install?) which was to determine why the keyboard shortcut for the terminal was not working. Searching I found reference to the "keyboard input method system" in Language Support. Settings Manager > Language Support

Apparently it was not fully installed, so I let it install itself, then looked at the aforementioned setting. It was set to Default. The suggestion was to change this setting to one of the others, then re-login and test. I chose IBus, logged in again and it worked! Then just out of curiosity, I tried the volume function keys and low and behold, they worked as well!

After a reboot, though, my shortcut keys for terminal stopped working again, however, the volume function keys still behave as expected.

Edit: again, it's either the shortcut keys or the volume function keys that work, never at the same time. Arg!

---


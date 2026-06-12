---
title: "keyboard key mapping udev rule trigged, executed xmodmap, but have no effect?"
date: 2016-12-30
forum: Hardware
---

### Post by zhangweiwu on 2016-12-30
```
$ cat /etc/udev/rules.d/kbc.rules 
SUBSYSTEM=="input", SUBSYSTEM=="input", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0f39", ATTRS{idProduct}=="0611", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/weiwu/.Xauthority", RUN+="/usr/bin/xinput set-button-map 'Lenovo Mice N700' 3 2 1"
SUBSYSTEM=="input", SUBSYSTEM=="input", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0f39", ATTRS{idProduct}=="0611", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/weiwu/.Xauthority", RUN+="/usr/bin/xmodmap -e 'keycode 49 = grave' -e 'keycode 9 = Escape'"

```
The first rule works fine. The second has no effect.

When I set the debug mode:
```
sudo udevadm control --log-priority=debug
```
I can see in the log that the xmodmap command is successfully executed:
```

Dec 31 11:46:27 systemd-udevd[2645]: RUN '/usr/bin/xmodmap -e 'keycode 49 = grave' -e 'keycode 9 = Escape'' /etc/udev/rules.d/kbc.rules:2
Dec 31 11:46:27 systemd-udevd[2645]: handling device node '/dev/input/event6', devnum=c13:70, mode=0660, uid=0, gid=106Dec 31 11:46:27 systemd-udevd[2645]: set permissions /dev/input/event6, 020660, uid=0, gid=106
Dec 31 11:46:27 systemd-udevd[2645]: creating symlink '/dev/char/13:70' to '../input/event6'
Dec 31 11:46:27 systemd-udevd[2645]: creating link '/dev/input/by-id/usb-Heng_Yu_Technology_Poker_II-event-kbd' to '/dev/input/event6'
Dec 31 11:46:27 systemd-udevd[2645]: creating symlink '/dev/input/by-id/usb-Heng_Yu_Technology_Poker_II-event-kbd' to '../event6'
Dec 31 11:46:27 systemd-udevd[2645]: creating link '/dev/input/by-path/pci-0000:00:14.0-usb-0:2:1.0-event-kbd' to '/dev/input/event6'
Dec 31 11:46:27 systemd-udevd[2645]: creating symlink '/dev/input/by-path/pci-0000:00:14.0-usb-0:2:1.0-event-kbd' to '../event6'
Dec 31 11:46:27 systemd-udevd[2645]: created db file '/run/udev/data/c13:70' for '/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:0F39:0611.0008/input/input29/event6'
Dec 31 11:46:27 systemd-udevd[2668]: starting '/usr/bin/xmodmap -e 'keycode 49 = grave' -e 'keycode 9 = Escape''
Dec 31 11:46:27 systemd-udevd[2645]: Process '/usr/bin/xmodmap -e 'keycode 49 = grave' -e 'keycode 9 = Escape'' succeeded.

```

My hypothesis:

1. udev rules can't affect running X session. => False, because the first, xinput rule, works.
2. xmodmap is not like xinput, it only affect the current window.  => False, I tried to open two windows of different X applications, and new xmodmap rules run from a third Gnome Terminal worked for both.

Note: If I google, many would suggest using xkb instead of xmodmap for remapping keys. I need one USB keyboard to have keys remapped, while the in-built keyboard's keys not remapped. xkb seems to affect both. If there is a way to remap keys using xkb selectively for different keyboards, I will use that instead of xmodmap.

Using Ubuntu 16.10, Thanks!

---

### Post by zhangweiwu on 2017-01-04
Two things happened. First, I found that my keyboard POKER II from VORTEX is programmable, so I programmed the two keys to work as each other, hence no longer need to run the xmodmap.

Regarding to the first udev rule, about remapping mouse buttons, I found that it should not be in udev, but in xorg.conf. From this: [http://superuser.com/questions/528528/x11-gnome-trackpoint-custom-button-mapping-not-working](http://superuser.com/questions/528528/x11-gnome-trackpoint-custom-button-mapping-not-working)

```

$ gsettings set org.gnome.settings-daemon.plugins.mouse active false

```

This would enable xorg.conf settings to be effective. I would think gnome operates on a layer on top of X so it shouldn't know what Xorg.conf configurations are, but to just obey it. It turns out Gnome have influence here.

> 
... not the end of the story, however, as Natty still uses gnome-settings-daemon to control mouse and keyboard settings. Usually, this is smart enough to get out of the way, but when it comes to mice, (specifically buttons) it will attempt to automatically ensure that your primary and secondary buttons are mapped to the system-wide left or right handed layout. In this particular case, we don't want that, so we need to turn this bit of functionality off.

In the end, since 1st udev rule should be moved to xorg.conf, and 2nd rule I couldn't make it work, I have removed both altogether. Now I am not using any udev rules.

Here is the xorg.conf:
```

$ cat /etc/X11/xorg.conf.d/00-mouse-remap.conf Section "InputClass"
   Identifier     "Bluetooth Mouse left-handed"
   MatchIsPointer "on"
   MatchProduct   "Lenovo Mice N700"
   Driver "evdev"
   # need this to be effective
   # gsettings set org.gnome.settings-daemon.plugins.mouse active false
   Option "ButtonMapping" "3 2 1 4 5 6 7 8 9"
EndSection

```

---


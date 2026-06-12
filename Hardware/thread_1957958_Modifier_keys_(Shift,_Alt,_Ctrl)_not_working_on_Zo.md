---
title: "Modifier keys (Shift, Alt, Ctrl) not working on Zowie Celeritas keyboard"
date: 2012-04-13
forum: Hardware
---

### Post by purity89 on 2012-04-13
I just got my new mechanical keyboard, a Zowie Celeritas Pro. But when I connected it, the modifier keys (Shift, Ctrl, Alt, Alt Gr, Right Shift, Right Ctrl) aren't working in Xubuntu (latest version, all updates installed). They work like they should in Windows 7, but not in Xubuntu. 

I tried searching, and found a couple of similar reports:
 - [http://www.moparisthebest.com/smf/index.php?topic=522338.0](http://www.moparisthebest.com/smf/index.php?topic=522338.0)
 - [https://bugs.archlinux.org/task/24505](https://bugs.archlinux.org/task/24505)
 - [https://bbs.archlinux.org/viewtopic.php?pid=933496](https://bbs.archlinux.org/viewtopic.php?pid=933496)

The comments on the bug report says it's some kind of driver issue, but they don't give any solutions. Does anyone here know what to do?

---

### Post by purity89 on 2012-04-14
I've been doing some testing with "showkey", and have some interesting results.

This is what happens when I write a capital t using my regular keyboard (where everything works):
```

keycode  42 press	# Shift press
Tkeycode  20 press	# t press
keycode  20 release	# t release
keycode  42 release	# Shift release

```

This looks very good. But look what happens when I do the same thing using my new keyboard
```

keycode  42 press	# Shift press
keycode  42 release	# Shift release
tkeycode  42 press	# Shift press
keycode  42 release	# Shift release
keycode  20 press	# t press
keycode  42 press	# Shift press
keycode  42 release	# Shift release
keycode  20 release	# t press

```

I've tried several times, and the behaviour is the same every time with the new keyboard. There's a lot of weird stuff happening before the "t" is pressed, and the shift is pressed and released before releasing the "t" again.

EDIT: This is what (the relevant part of) my xorg log file looks like:

```

[    17.200] (II) config/udev: Adding input device Zowie Zowie&#2485;&#38326;&#33026;&#38242; (/dev/input/event7)
[    17.201] (**) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Applying InputClass "evdev keyboard catchall"
[    17.201] (II) Using input driver 'evdev' for 'Zowie Zowie&#2485;&#38326;&#33026;&#38242;'
[    17.201] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.201] (**) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: always reports core events
[    17.201] (**) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Device: "/dev/input/event7"
[    17.201] (--) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Found keys
[    17.201] (II) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Configuring as keyboard
[    17.201] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input7/event7"
[    17.201] (II) XINPUT: Adding extended input device "Zowie Zowie&#2485;&#38326;&#33026;&#38242;" (type: KEYBOARD)
[    17.201] (**) Option "xkb_rules" "evdev"
[    17.201] (**) Option "xkb_model" "pc105"
[    17.201] (**) Option "xkb_layout" "no"
[    17.201] (II) config/udev: Adding input device Zowie Zowie&#2485;&#38326;&#33026;&#38242; (/dev/input/event9)
[    17.201] (**) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Applying InputClass "evdev keyboard catchall"
[    17.201] (II) Using input driver 'evdev' for 'Zowie Zowie&#2485;&#38326;&#33026;&#38242;'
[    17.201] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.201] (**) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: always reports core events
[    17.201] (**) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Device: "/dev/input/event9"
[    17.201] (--) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Found keys
[    17.201] (II) Zowie Zowie&#2485;&#38326;&#33026;&#38242;: Configuring as keyboard
[    17.201] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.1/input/input9/event9"
[    17.201] (II) XINPUT: Adding extended input device "Zowie Zowie&#2485;&#38326;&#33026;&#38242;" (type: KEYBOARD)
[    17.201] (**) Option "xkb_rules" "evdev"
[    17.201] (**) Option "xkb_model" "pc105"
[    17.202] (**) Option "xkb_layout" "no"

```

---

### Post by purity89 on 2012-04-14
I just found a "solution". By using two adapters, USB-to-PS/2, and then a PS/2-to-USB, my modifier keys are now officially working!

Before:
```

$ lsusb
[...]
Bus 007 Device 002: ID 2345:0101  
[...]

```
Now:
```

$ lsusb
[...]
Bus 007 Device 005: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter
[...]

```

The media keys aren't working, but I'm only using this laptop temporarily while I wait for my RMA'd motherboard, so that I can live with!

---


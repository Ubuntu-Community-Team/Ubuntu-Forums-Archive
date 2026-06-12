---
title: "Touchpad TapButtonX properties after resume from sleep"
date: 2012-05-23
forum: Hardware
---

### Post by v6ak on 2012-05-23
Hello,
I've a Dell Inspiron 17R laptop with AlpsPS/2 ALPS DualPoint TouchPad, controlled by synaptics driver. I've some troubles with setting TapButtonX (especially TapButton2) properties. Well, I can set it, but it is overriden by Gnome Settings Daemon after resume from sleep.

It seems to be a known and solved issue: [http://ubuntuforums.org/archive/index.php/t-1576714.html](http://ubuntuforums.org/archive/index.php/t-1576714.html)

I'd preffer an noninterventing settings daemon. So I've tried to let GSD not to config my touchpad. But I can't find the key in gconf-editor. (See the attachment.) I've found a simillar key, but disabling does not have the effect.

Another approach is not to use GSD. When I was using Archlinux or Gentoo with Gnome 2, I didn't use GSD. But I don't know how to start Gnome Power Manager in such case with Gnome 3. I'm also not sure if I can remove or it in Ubuntu (with Openbox + Unity 2D shell + Unity 2D panel service).

EDIT: I've created another workaround (synaptics-clicks is an app for configuring the touchpad):
```
(dbus-monitor --system 'path=/org/freedesktop/UPower,interface=org.freedesktop.UPower,member=NotifyResume' | while read _; do synaptics-clicks; echo SC; done)&
```

---


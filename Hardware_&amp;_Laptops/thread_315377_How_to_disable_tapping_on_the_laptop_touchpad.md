---
title: "How to disable tapping on the laptop touchpad"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by zoffmann on 2006-12-09
Hi,
I am using edubuntu 6.10 and I would like to disable tapping on my touchpad.

How do I do it?

---

### Post by bapoumba on 2006-12-09
Looks like you have different ways to do this, depending on the laptop.

[http://ubuntuforums.org/showthread.php?t=76585]("http://ubuntuforums.org/showthread.php?t=76585")
[http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/]("http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/")

More infos in a [bug report]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/47971")

---

### Post by sandman652001 on 2006-12-09
If you have a synaptics touchpad
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf)
Hope it helps

---

### Post by TheWizzard on 2006-12-09
> **sandman652001 said:**
> If you have a synaptics touchpad
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf)
Hope it helps

you can use qsynaptics to modify the behaviour of your touchpad. make sure you run ```
qsynaptics -r

```at login. the way to do that depends on if you're using kde or gnome.

---


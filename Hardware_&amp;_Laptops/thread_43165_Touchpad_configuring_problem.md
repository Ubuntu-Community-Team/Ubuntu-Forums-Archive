---
title: "Touchpad configuring problem"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by Warren on 2005-06-21
I have an HP Pavilion ze4400 with a synaptics touchpad built in.  I installed Ubuntu today and find that the tap-to-click feature is far too sensitive.  That is, most times I get too close to the touchpad or am trying to make short, precise movements, it clicks somewhere I don't want it to.

Does anyone know how to disable tap-to-click entirely?

---

### Post by alive on 2005-06-22
I have a similar problem. I tried using ksynaptics from the universe repository (I use Gnome but somehow I can access the KDE Control Center anyway). None of my changes in it had an effect. Help would be appreciated.

---

### Post by Warren on 2005-06-26
I **eventually** found what I needed to do.  If you have a synaptics touchpad, go here.

[http://ubuntuforums.org/archive/index.php/t-3994.html](http://ubuntuforums.org/archive/index.php/t-3994.html)

Make sure you use the filename "xorg.conf" instead of what the howto specifies if you use the Hoary Hedgehog version of Ubuntu.

---


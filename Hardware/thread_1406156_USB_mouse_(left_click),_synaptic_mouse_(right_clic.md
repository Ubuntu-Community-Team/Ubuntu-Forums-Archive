---
title: "USB mouse (left click), synaptic mouse (right click)"
date: 2010-02-13
forum: Hardware
---

### Post by claudio4j on 2010-02-13
Hi guys, I have a usb mouse where I use it with the left hand, and have swapped the main click to be the left click. no problem.
The synaptic mouse is more intuitive for me to use the right click, as normal.

Before the 9.10 release, xorg.conf was modified to make this configuration works, by tweaking the InputDevice section.

I read the people can insert a new xorg.conf, but I feel it is going to disrupt the normal xorg behavior in the near future. I believe the kubuntu or xorg developers have a good motive to not let the user change the xorg configuration by hand. So I want a clean and supported way to change the mouse click behavior.

The 9.10 release, doesn't have the xorg.conf. How am I supposed to change the synaptic click behavior ?

There is a gsynaptics application, but it doesn't change the click button behavior.

Thanks

Claudio

---

### Post by Ayuthia on 2010-02-13
If I remember correctly, the file should be located in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi.  You should make a copy of it and modify it in /etc/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/20thirdparty/
```
You can then edit the file:
```
gksu gedit /etc/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

There should be some examples in there on how to add things to the file.  The reason for the change was because hal was going to be used to configure files instead of xorg.conf.  It allowed for hot plugging if I recall correctly.  However, hal is now deprecated so Lucid is going to be using udev.  

Hope that helps.

---


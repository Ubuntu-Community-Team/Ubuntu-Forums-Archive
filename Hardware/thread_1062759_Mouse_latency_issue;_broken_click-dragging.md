---
title: "Mouse latency issue; broken click-dragging"
date: 2009-02-07
forum: Hardware
---

### Post by Whitefall on 2009-02-07
I have a problem similar to the one described in [https://bugs.launchpad.net/ubuntu/+bug/144277](https://bugs.launchpad.net/ubuntu/+bug/144277): the mouse movement and mouse button clicks aren't synchronized, which is very annoying whenever I quickly drag-and-drop something, or want to select some text etc.

I was able to fix this by adding `Option "AutoAddDevices" "false"' to the ServerLayout of my xorg.conf, but this is not really a solution because it also affects the keyboard (disables the multimedia keys).

Apparently, with AutoAddDevices set to false, the "mouse" driver is used instead of the "evdev" driver. I guess I have to change the hal configuration to use the "mouse" driver. I tried adding an fdi file in /etc/hal/fdi/policy containing
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">mouse</merge>
    </match>
  </device>
</deviceinfo>
```
But this just freezes the X server as soon as I reconnect the mouse.

I'm using Ubuntu 8.10 (relatively fresh install) and a normal Logitech USB mouse.

---


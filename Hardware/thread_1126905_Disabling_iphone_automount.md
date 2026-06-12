---
title: "Disabling iphone automount"
date: 2009-04-15
forum: Hardware
---

### Post by n8wood on 2009-04-15
Hi, I'm working on udev scripts that allow me to automatically sync my iphone with a VirtualBox VM that starts/shuts down when I connect/disconnect my phone. So far the scripts seems to be working, but I am getting error messages that makes me think GNOME is trying to automount the device:

"Unable to mount Apple, Inc. iPhone
Error initializing camera: -60 : Could not lock the device"

I looked into gnome-volume-manager options in gconf, and looked at the Removable Devices preferences, neither seemed to help.

Any ideas where I can look to stop this from automounting?

---

### Post by n8wood on 2009-04-15
I disabled automount entirely in Nautilus by using gconf-editor and unchecking app > nautilus > preferences > media_automount.

Not a perfect solution, but I can still many mount stuff in Nautilus.

---

### Post by d0b33 on 2009-08-07
I get the same error:
"Unable to mount Apple, Inc. iPhone"

This happened after trying iFuse, before iFuse I never got this message.

Uninstalling iFuse did not solved the problem

Help would be appreciated... :(

---

### Post by lesta on 2009-11-01
I had the same problem! You have to uninstall some of the the iFuse dependencies: libusbmux, libiphone, libplist. I'm pretty sure that the problem is caused by libusbmux0 and nautilus usb automount conflict.

You can find some useful information about iphone/ipod syncing from this blog: [http://marcansoft.com/blog/](http://marcansoft.com/blog/)

> **d0b33 said:**
> I get the same error:
"Unable to mount Apple, Inc. iPhone"

This happened after trying iFuse, before iFuse I never got this message.

Uninstalling iFuse did not solved the problem

Help would be appreciated... :(

---


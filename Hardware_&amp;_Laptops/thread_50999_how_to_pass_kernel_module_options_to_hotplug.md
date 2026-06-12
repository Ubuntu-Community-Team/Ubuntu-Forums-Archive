---
title: "how to pass kernel module options to hotplug?"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by stanwebber on 2005-07-22
my webcam uses the zr364xx driver in addition to whatever usb modules are required.  hotplug automatically loads the proper modules when i plug my camera in, but i have to manually add the following parameters for my camera:

modprobe zr364xx mode=2 hardbright=1

is there a way to pass the above options to hotplug so they are automatically added whenever i plug in my camera?

---

### Post by mo_x on 2005-07-22
Create a file in /etc/moprobe.d (for example /etc/modprobe.d/zr364xx) and put the following line in it:
options zr364xx mode=2 hardbright=1

See also the man page for modprobe.conf

---


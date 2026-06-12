---
title: "Touchpad scrolling/gestures on Vaio VPCSB"
date: 2011-06-04
forum: Hardware
---

### Post by rwankar on 2011-06-04
I've installed 11.04 with all available updates.

1. /var/log/Xorg.0.log shows touchpad found. Type is AlpsPS/2 ALPS Glidepoint.

2. No scroll vertical/horizontal/2-finger. Move cursor and click works.

I've tried adding i8042.nopnp to grub. Making it a PS/2 mouse by adding "options psmouse proto=imps" to /etc/modprobe.d/psmouse.conf works but erratically.

---

### Post by liufu_ty on 2011-07-26
I have exactly the same problem. And it is very annoying something when I type the touchpad is still working...
Does anyone knows how to perfectly solve this problem? Thanks

---

### Post by liufu_ty on 2011-07-26
Seems it is a bug as here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051)

Hope they can fix it soon ...

---

### Post by rwankar on 2011-10-23
A fix is now available. Try the patch provided at the very end of the bug report mentioned above.

---


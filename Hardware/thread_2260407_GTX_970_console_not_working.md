---
title: "GTX 970 console not working"
date: 2015-01-11
forum: Hardware
---

### Post by orlenok41 on 2015-01-11
Hello,

I just built new system with an NVIDIA GTX 970 card. I am unable to switch to any of the CTRL+ALT+F? screens: all I get is a blank screen. I managed to install nvidia drivers through SSH and everything works well on X, however, still nothing on the console. Is there a workaround? I suspect this is due to the framebuffer and tried disabling it by blacklisting vesafb in /etc/modprobe.d/blacklist-framebuffer.conf, however, it still gets loaded for some reason.

Many thanks in advance for any advice on this.

---


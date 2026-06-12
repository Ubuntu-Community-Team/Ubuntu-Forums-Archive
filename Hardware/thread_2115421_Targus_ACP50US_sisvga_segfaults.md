---
title: "Targus ACP50US sisvga segfaults"
date: 2013-02-12
forum: Hardware
---

### Post by jimbolaya on 2013-02-12
I'm currently running 12.04 64-bit and I was looking at hooking up my Targus ACP50US for playing around with it.  I wanted to see how well the VGA port was supported and I was happy to see that it was supported automatically (at least the drivers loaded) and I didn't have to mess around with patching them as described in this post:
[http://ubuntuforums.org/showthread.php?t=1639601](http://ubuntuforums.org/showthread.php?t=1639601)

However, after creating the xorg.conf.usbvga and running 

Xorg :1 -config /etc/X11/xorg.conf.usbvga -sharevts,

Xorg segfaults.  I'm not sure where to go from here, but if any one has any ideas on how to test this, I'd love to hear about them.  I can also post the log file somewhere.

James

---


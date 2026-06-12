---
title: "Huge fonts problem with i945GM"
date: 2009-11-10
forum: Hardware
---

### Post by disya2 on 2009-11-10
Hi,

I have "huge fonts" issue described in this topic [http://ubuntuforums.org/showthread.php?t=1309363](http://ubuntuforums.org/showthread.php?t=1309363) as well as here [http://ubuntuforums.org/showthread.php?t=1208199](http://ubuntuforums.org/showthread.php?t=1208199) and many other places.

I've been using Ubuntu 8.04 and after gradually upgraded to 8.10-9.04-9.10 the problem appeared. The issue appears in some non-gnome applications such as Emacs 23 or Google Earth. I tried many things: creating ~/.Xresources with Xft.dpi:96, system-wide /etc/X11/Xresources, adding -dpi 96 to /etc/X11/xinit/xserverrc, setting DisplaySize in xorg.conf along with Option "NoDDC". None has solved the issue. The only way it works is when I stop xserver and then run startx -- -dpi 96 from console.


Thanks,
Denis

---


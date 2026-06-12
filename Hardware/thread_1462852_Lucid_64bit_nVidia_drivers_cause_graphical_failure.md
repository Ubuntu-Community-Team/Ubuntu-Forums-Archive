---
title: "Lucid 64bit nVidia drivers cause graphical failure"
date: 2010-04-26
forum: Hardware
---

### Post by seanlano on 2010-04-26
On Lucid 64bit testing versions on my desktop Acer Aspire PC with nVidia card (not sure what type), if I install the "nvidia-current" package to enable 3D acceleration, the computer then fails to boot to a graphical environment. I can see the plymouth splash during boot, but after that the screen flickers a few times and dumps me to a tty display. The only way to get back to a working system is to uninstall "nvidia-current" and restart (which obviously leaves me without 3D acceleration). On the same system using 32bit Lucid this was not a problem. I have not tried earlier 64bit releases. Kernel is 2.6.32-21. 

What could be causing this to happen?

---

### Post by stee2000 on 2010-04-26
Have you looked at /etc/X11/xorg.conf ?  Do you have such a file?
Can you run nvidia-xconfig as root?

---


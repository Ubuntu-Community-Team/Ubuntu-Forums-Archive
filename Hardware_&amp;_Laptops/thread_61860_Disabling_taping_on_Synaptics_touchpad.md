---
title: "Disabling taping on Synaptics touchpad"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by Polbit on 2005-09-02
My first post here, I just installed Ubuntu 5.04 on my Dell D600, and love it!! First Linux distro that I'm comfortable with, and will probably finally replace my WinXP setup.

Anyway, my question is: how can I disable the taping on the touchpad? It's a Synaptics touchpad... Can't find any settings for it anywhere...

Thanks!!

---

### Post by MdaG on 2005-09-02
[QUOTE=Polbit]My first post here, I just installed Ubuntu 5.04 on my Dell D600, and love it!! First Linux distro that I'm comfortable with, and will probably finally replace my WinXP setup.

Anyway, my question is: how can I disable the taping on the touchpad? It's a Synaptics touchpad... Can't find any settings for it anywhere...

Thanks!![/QUOTE]

I've got the same problem. I've got a DELL D800. I know it's possible to disable the tapping feature a <time> after each keystroke. I've done that on my Gentoo system using syndaemon. But Ubuntu doesn't allow me to do that. I get the following.

> $ sudo syndaemon
Can't access shared memory area. SHMConfig disabled?

I've enabled SHMConfig in my touchboard input section in xorg.conf.

---

### Post by nic2 on 2005-09-02
[QUOTE=Polbit]My first post here, I just installed Ubuntu 5.04 on my Dell D600, and love it!! First Linux distro that I'm comfortable with, and will probably finally replace my WinXP setup.

Anyway, my question is: how can I disable the taping on the touchpad? It's a Synaptics touchpad... Can't find any settings for it anywhere...

Thanks!![/QUOTE]
Have you read the applicable readme file located in /usr/share/doc/xorg-driver-synaptics ?

---

### Post by Polbit on 2005-09-02
Thanks, I'm still learning where everything is, so didn't think of looking into that particular directory. Having said that, according to the README, setting MaxTapTime to 0 in /etc/X11/xorg.conf did not do anything for me...  Neither did playing with TapButton1,2,3...

Oh well, it's not that big of a deal, I gotta get my Linksys WiFi card working now, then I can worry about other little issues :)

---


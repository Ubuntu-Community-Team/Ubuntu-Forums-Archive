---
title: "Acer turns off display"
date: 2010-09-02
forum: Hardware
---

### Post by rasmus91 on 2010-09-02
Hello there.

Sometime ago i installed ubuntu, and started tweaking it to my liking, i ran into a problem though, i read somewhere that the restricted nvidia driver offers more performance than the novaeu so i decided to install the restricted.

i did the usual system->admin->hardware drivers

and chose the recommended driver. it told me that i needed to reboot to activate it, so i did. So when the ubuntu splash screen should show up the display just turned black, and nothing happens.

so i figured it had something to do with the nvidia driver; I booted from a flashdrive and chrooted my linux partition, and used ```
sudo apt-get remove nvidia*
```

Then it told me that removing the nvidia driver would free up 135 MB, Y/N and i pressed Y. and when it was done i rebooted.

Still the display is just black when i get to the splash/login screen. Does anyone have an idea?
Is it because i have to reenable the novaeu driver?

Perhaps you should know that my computer is an Acer Aspire 5745G

Grphics are Nvidia Geforce GT 330m Cuda

Help is appreciated.

---

### Post by rasmus91 on 2010-09-05
Seems i got it working my self...

Thank you Ubuntu for safe graphics mode!

---


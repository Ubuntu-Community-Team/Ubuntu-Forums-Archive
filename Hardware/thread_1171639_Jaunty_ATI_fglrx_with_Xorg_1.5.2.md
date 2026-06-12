---
title: "Jaunty: ATI fglrx with Xorg 1.5.2"
date: 2009-05-27
forum: Hardware
---

### Post by xaviermerino on 2009-05-27
Hi!.. I successfully managed to downgrade Xorg 1.6 to Xorg 1.5.2 in Jaunty, however I am not getting something on the screen! I struggled for hours to downgrade and finally did, I also installed the ATI Propietary Drivers for my ATI Radeon X1200, and did a reboot. ATI changed the Xorg.conf file with another one, which seemed very complicated to understand, it didn't work either. So I decided to do an xfix, it restored the xorg.conf, and it didn't work, I added a couple of lines..

```

Section "Module"
[INDENT]load "dri"[/INDENT]
[INDENT]load "GLcore"[/INDENT]
EndSection

Section "Device"
[INDENT]Identifier "Configured Video Device"[/INDENT]
[INDENT]Drivers "fglrx"[/INDENT]
EndSection

```

Using Xorg 1.6, the driver must be radeon, otherwise I get no screen. So I supposed that by installing the fglrx drivers I could use the drivers. But I don't. 

I think I have tried everything. How am I supposed to make ATI work with Xorg 1.5.2 in Jaunty?

---

### Post by Sepero on 2009-09-22
This guide allowed me to easily downgrade Xorg and get this problem solved:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---


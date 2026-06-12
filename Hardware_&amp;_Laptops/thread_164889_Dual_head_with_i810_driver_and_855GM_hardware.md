---
title: "Dual head with i810 driver and 855GM hardware"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by TheSoko on 2006-04-23
I'm trying to follow [this HOWTO]("http://ubuntuforums.org/showthread.php?t=155762&highlight=i810+dual+head") on my Dell 700m but when I type the command

```
dpkg-buildpackage -rfakeroot -b
```

I get this error...

```
i810_driver.c:77:16: error: Xv.h: No such file or directory
```

Any ideas on how this file disappeared, or how to fix it? :/

---

### Post by TheSoko on 2006-05-03
Anybody?

I tried editing the Makefile in the same directory as i810_driver.c, so that the extensions include directory points to /usr/include/X11/extensions but now I get a bunch of errors relating to struct _I830Rec, which doesn't appear to be declared in i810_driver.c... Anybody familiar enough with this? Or could I just download the generated .deb file from somewhere?

---

### Post by pestilence4hr on 2006-05-09
Try

```
sudo aptitude install x11proto-video-dev
```

I think this should have been installed by default if you ran ```
sudo apt-get build-dep xserver-xorg-driver-i810
```  I highly recommend you run this before continuing to attempt the build.

---

### Post by TheSoko on 2006-05-18
I still get the same error...

---


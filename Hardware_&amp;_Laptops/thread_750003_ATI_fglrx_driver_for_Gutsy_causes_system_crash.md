---
title: "ATI fglrx driver for Gutsy causes system crash"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by mdhicks1 on 2008-04-09
I followed a tutorial to enable 3D effects, and ever since my computer will not let me log in. When I input my user name and password, it goes to a black screen with some system info, then immediately goes back to the log-in screen. Fail-safe is the only way I can get my computer to work.

Here is the tutorial I followed:
[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)
(post #7, for fresh install of Gutsy)

My machine is an Inspiron 8500 with what I believe is a Mobility Radeon 9600 video card.

I'm very new at Linux, so please be patient with me. Thanks for any help you can give!

---

### Post by Yellow Pasque on 2008-04-09
It would be better to use the open-source radeon driver or the newer ATI driver that doesn't require XGL (Method 2 here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) )

If you decide to try one of those routes remember to uninstall XGL first:
```
sudo apt-get remove xserver-xgl
```

---

### Post by mdhicks1 on 2008-04-09
Uninstalling XGL fixd the problem, so I can log-in without being in Failsafe GNOME now. Thanks!

I'm still having one problem with getting the driver for my ATI card, though. The restricted ATI driver has never appeared in my Restricted Drivers Manager. Is there any way I can make that happen?

Thanks again!

---

### Post by Yellow Pasque on 2008-04-09
If you want to use 3D effects, you'll need to use the driver from ATI's site, not the version supplied with Ubuntu. See the link in my last post for directions.

For reference, the Ubuntu restricted driver might not be compatible with a M.R. 9600, or you might not have the restricted repo enabled in System -> Adminstration -> Software Sources.

---


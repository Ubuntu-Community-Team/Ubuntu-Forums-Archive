---
title: "Disable 3d acceleration"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by adrawer on 2005-07-07
I followed some steps on the wiki page to enable 3d acceleration for my ati x300 video card for my laptop.  However, my system has become very unstable, freezing at random times.  I was wondering how i would disable 3d acceleration.  thanks

Andrew

---

### Post by mmeehan on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				From 

$ man via

Add 

       Option "NoAccel" "true"

To the device section of your /etc/X11/xorg.conf file.

However, this will also disable 2D acceleration as well.

---


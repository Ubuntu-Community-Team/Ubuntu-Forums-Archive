---
title: "Ati Suspend"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by Takayakon on 2007-12-08
Ever since I have tried 7.10, 99% of all my hardware worked perfectly and the one thing that doesn't work is ATI's fault I would guess. Suspend works flawless when I use the default vesa driver. Once I install the ATI Propreitary it won't even suspend, the screen goes blank. From what I've read it's not something I can fix. 

Anyway, is there I way I can get 1280x768 resolution without installing the ATI Driver? I'm not sure if this is even possible, but I would appreciate it if anyone could inform me.

Laptop Specs
Asus W3J
ATI Technologies Inc M56P [Radeon Mobility X1600]
14" Widescreen, 1280x768

---

### Post by Takayakon on 2007-12-09
I managed to find a solution, apparently it involved blacklisting the part of the ati driver that allows 3d, this however does turn off 3d, which is fine by me for now.

This is where I found it in case anyone else is interested.
[http://justincaseyouwerecurious.blogspot.com/2007/10/ubuntu-gutsy-ati-suspend-workaround.html](http://justincaseyouwerecurious.blogspot.com/2007/10/ubuntu-gutsy-ati-suspend-workaround.html)

> 
The latest release of Ubuntu (Gutsy) which is in beta testing right now has a problem where laptops with ATI graphics cards will hard hang when you attempt to suspend.  The screen goes blank but the suspend light (usually a moon or something) just flashes forever.

Here is bug with the insanely long bug comment thread:

[http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/](http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/)

Here is the workaround:

Create this file:
   /etc/modprobe.d/blacklist-fglrx

Put this in it:
   blacklist fglrx

Reboot. 

This will allow you to continue to use the fglrx X.org driver but without the kernel module which causes the problem with suspend. .  This means you get 2D acceleration but not 3D.  So no cool Compiz eye candy.  But at least you can put your laptop to sleep. 


---


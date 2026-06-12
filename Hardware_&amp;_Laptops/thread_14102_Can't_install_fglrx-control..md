---
title: "Can't install fglrx-control."
date: 2005-02-04
forum: Hardware &amp; Laptops
---

### Post by swirvi on 2005-02-04
So I followed the Binary Drivers How-To, and everything seems to have worked. I would like to install this last package so I can setup my second monitor. Anyway apt complained about a dependancy on libqt3c102-mt, which is uninstallable. Searching the forums I found this post on the matter. I followed the suggestion of using Synaptic to install fglrx, but that doesn't seem to make a difference. As I understand it, libqt3c102-mt is unessential for fglrx-control. How to I tell the system to ignore the dependancy? 


> **wallijonn]You should use SPM to install fglrx-control and fglrx-driver. This is because it will also force you to install [COLOR=BLUE]libqt3c102-mt 3:3.2.3-ubuntu1[/COLOR]. The chances are that [COLOR=BLUE]xlibmesa-gl and xlibmesa-glu[/COLOR] are already installed said:**
> fglrx-dev[/COLOR].

The path for mice is /dev/input/mice

You should NOT use the external AGPGART. (Are nVidia users forced to use the external AGP GART?)

Also **be aware that you should be using the default i386 kernel**. If you install an i686 kernel it may not work. (I learned this the HARD way - I spent quite a few hours chasing down DRI not being enabled). I believe this is because the i686 kernels are at 2.6.7-13 and not 2.6.8-1.

The easiest way to test, besides running glxgears, is to set your screensaver to ATunnel. If it does not run quick and smooth - chances are that your /var/log will show XFree86.0.log as being "DRI not enabled" (towards the end of the file). In that file you should see a lot of 'fglrx' entries. If you do not see them - fglrx is not installed (for whatever reason - most probably a wrong kernel). 

Before running fglrxconfig copy the /etc/X11/XF86Config-4 to your home directory.

If it crashes upon reboot, sudo cp XF86Config-4 /etc/X11
because when you log in to root you will automatically be at /home/<username>.
Then 
[COLOR=RED]shutdown -r now[/COLOR]
should reboot the PC. (You could probably init to level 2 and restart the window, but a reboot is probably safer).

BUT - since you are already at a root prompt, just issue a 
[COLOR=RED]fglrxconfig[/COLOR]
command to rerun and write a new XF86Config-4 file. Then reboot.

.

Sorry if this is the wrong forum. This was overlooked in software support.

---

### Post by malegria on 2005-02-05
I suggest you refer to this site to get your fglrx driver going. 
[HTML]http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html[/HTML]
I did it, and it all came together like gravy. Sure, this way will take about 20 minutes to do, but it's worth the wait to get something going *right.*

And at step 4 use the "make-kpkg" option, not the previous two (4.1, 4.2)

And another thing. If you want to find out your current kernel type, at a terminal type:
 ```
uname -r 
```

Run into any trouble, hit me back.

---


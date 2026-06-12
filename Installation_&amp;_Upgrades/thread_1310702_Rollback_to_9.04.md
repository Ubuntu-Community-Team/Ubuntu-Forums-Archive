---
title: "Rollback to 9.04"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by bcbotha on 2009-11-02
I installed ubuntu 9.04 on my laptop and a couple of days ago run the update to 9.10 through update manager. but now my ATI X1200 graphics card is no longer supported. Is there any way to get it working? If not how do I rollback the update?

Thanks

---

### Post by jjcv on 2009-11-02
I don't know much about the graphic's driver.   

There is no way to roll back to a previous version but your old kernel may still be installed which supports the old driver.  When it boots pres ESC to see if it is listed in GRUB and boot from it to give it a try.

Otherwise you will need to do a fresh install of 9.04.

---

### Post by antiram on 2009-11-02
is no longer supported from fglrx driver. But there is a open source driver which should work.
install package "xserver-xorg-video-ati" and rename (for backup) /etc/X11/xorg.conf

you can also make a new xorg.conf with "sudo dpkg-reconfigure -phigh xserver-xorg", but not needed.

there is also a second open source driver "xserver-xorg-video-radeonhd"

---

### Post by ROUBOS on 2009-11-02
yes thats what I've been reading now. :(

Seems like Compiz is working normally... and in 9.10 its working by default.

So I guess its all ok as is...

EDIT>>> So how to we test that 3D is working properly?

---

### Post by ajgreeny on 2009-11-02
There have been issues with the ati driver in 9.10 that have yet to be fully solved, which may be affecting your system.
See:-
[http://ubuntuforums.org/showthread.php?t=1304961](http://ubuntuforums.org/showthread.php?t=1304961)
[http://ubuntuforums.org/showthread.php?t=1305306](http://ubuntuforums.org/showthread.php?t=1305306)
[http://ubuntuforums.org/showthread.php?p=8199471#post8199471](http://ubuntuforums.org/showthread.php?p=8199471#post8199471)

---

### Post by ROUBOS on 2009-11-02
Well compiz works fine here. ATI Radeon X1950Pro 512mb AGP. 
Just sometimes seems slow etc. 
Oh well my experience with Linux and ATI has been a bad one.
ATI seem nice and stable under Window$ and I prefer ATI for my gaming.
Too bad it has to disapoing us once more under Linux :(

---

### Post by antiram on 2009-11-02
i buy only ati cards since 10 years because the good open source driver.

---

### Post by ajgreeny on 2009-11-02
> **antiram said:**
> i buy only ati cards since 10 years because the good open source driver.
I might have agreed until this problem arose, but it seems to be a bit of a difficult one.

I imagine there are several new users who have given up when their computer showed the black screen instead of wallpaper.  It would have been a lot better if compiz were not switched on by default at install, at least then the new users may have realised that their machine was not capable of running it at the moment.

---


---
title: "How to install the xorg &quot;radeon&quot; driver?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by nkzealot on 2006-03-25
This question seems to be silly, but it is really the one that has been confusing me for quite a long time.

I installed ubuntu  about 6 months ago on my thinkpad X32, which has a ati mobility radeon 7000 on it. I searched the thinkwiki, and found what I need is the xorg radeon driver and the dri module. However, I could not find the "radeon" driver package in the respository. Also, I could not find this driver when trying "dpkg-reconfigure xserver-xorg". I really do not know if this was simply because the ubuntu team had not compiled this driver themselves?? Or, I don't need to install a "radeon driver" package at all, just changing "ati" to "radeon" in the xorg.conf is okay?

---

### Post by claes on 2006-03-25
Yes that's all you need to do. That is to change ati to radeon in /etx/X11/xorg.conf.

Claes

---

### Post by nkzealot on 2006-03-25
Thanks Claes.

I just modified the xorg.conf. But the results given by glxgears do not change, the values are very low ( below 200). Is this the case for my card?

---

### Post by el_rata on 2006-03-25
i think is not radeon, is fglrx ... make a dpkg-reconfigure xserver-xorg, and select fglrx from the list, the you have to install the drives from the ati homepage ... 
NOTE: i'm having some problems by doing this ...

---

### Post by nkzealot on 2006-03-25
to el_rata:

I have searched the ati home page. the fglrx driver does not support mobility radeon 7000 and 7500.

---

### Post by LordRaiden on 2006-03-26
I think you want the OSS drivers from the nice people at dri.freedesktop.org. 

[http://dri.freedesktop.org/snapshots/]("http://dri.freedesktop.org/snapshots/")
Install the latest common package and the radeon drivers (scroll to the bottom).

The latest at the moment are

[http://dri.freedesktop.org/snapshots/common-20060325-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/common-20060325-linux.i386.tar.bz2")
 [http://dri.freedesktop.org/snapshots/radeon-20060325-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/radeon-20060325-linux.i386.tar.bz2")

Pretty much installation is composed of extracting the packages, then installing but here is a quick guide.

1) extract both packages (home directory is fine)
2) navigate to the common package's directory (cd common-20060325-linux.i386)
3) do 
```
sudo ./install.sh
``` 
4)navigate to the radeon package directory
5) do
```
sudo ./install.sh
``` 6) make sure your xorg.conf file has 'radeon' as the driver not 'ati'.
7) Reboot / Restart X
8) enjoy.

---


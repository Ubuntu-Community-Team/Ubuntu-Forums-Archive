---
title: "Customize Default Installed Package List"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2008-12-26
I have read over documents talking about how to customize the Ubuntu installer. Such as:

How to Customize the Ubuntu Desktop CD
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

InstallCDCustomization
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

This actually is as close to what I an needing info about as I have found:

Contents of the preconfiguration file \ Apt setup
[https://help.ubuntu.com/8.04/installation-guide/i386/preseed-contents.html#preseed-apt](https://help.ubuntu.com/8.04/installation-guide/i386/preseed-contents.html#preseed-apt)

I need to review all of the packages that are installed by default with the GUI normal install CD, and leave lots of things out... Open Office, the Games, ComPiz, etc... Just arrive at a lean install of Linux, with Gnome, and basic utilities. And yes I wish to modify the normal desktop install CD, not the alternate CD. I would prefer installing via the GUI and not text only interface.

Also I will (once I get this far) need to add certain packages that I have .deb packages for, just they are not in Ubuntu repositories, so how to include those on the CD and in the default package list.

I currently use Ubuntu 8.04, but for this work I think starting research @ 8.10 version would be the best direction.

---

### Post by Coder543 on 2008-12-26
Sounds to me like you want [Insta-Linux]("http://www.instalinux.com") which allows you to do all that AFAIK.

---

### Post by mdlueck on 2008-12-26
I just looked over that site, instalinux.com.

A handy interface, but I saw no way to start with Ubuntu Desktop, and see "if I do not install this package then what else will be affected" type of thing.

For example, I can purge almost all Evolution packages other than the one that ubuntu-desktop relies on.

That sort of thing I would like to do...

Maybe start with a default install and simply purge away until I arrive at the concise package list. Then export that list with dpkg at the command line.

So, how then to invent an installation path: ubuntu-minimal for example.

And too, how to include those .deb packages that I have that are not part of the Ubuntu repository system.

Thanks!

---


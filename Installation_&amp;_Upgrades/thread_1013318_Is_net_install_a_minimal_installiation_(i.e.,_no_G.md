---
title: "Is net install a minimal installiation (i.e., no GUI)"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by bill-linux on 2008-12-16
I have a Dell D400 laptop. It has no CD so I had to do a net install. I made a bootable USB using unetbootin (really GREAT program), booted, then did the net install. When I started the machine there is no GUI (no gdm, x server, etc.) Is a net-install minimal, or did I miss some box to check for "desktop environment"? (I can also all the missing stuff, but if I missed a box I'd prefer at this point to reinstall.

As a side note: Ubuntu (or unetbootin's USB) mess up grub. It directed it toward hd(1,0) instead of hd(0,0) -- easy enough to figure out once you know what is going on.

---

### Post by Partyboi2 on 2008-12-16
You should have a gui desktop if you installed the desktop version of Ubuntu

---

### Post by bill-linux on 2008-12-16
well... it didn't! When you use unetbootin it has several "build-in" distros that it will make a usb for --- actually it goes to their web site and grabs the files. I choose 8.04_netinstall. (I had earlier used unetbootin's debian netinstall: It installed a GUI just fine!) It gets the iso (or files) from:

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux)

In general I can find little about the netboot image from the ubuntu site.

BTW: In regards to installer putting grub on the usb see: [https://bugs.launchpad.net/unetbootin/+bug/255017](https://bugs.launchpad.net/unetbootin/+bug/255017)

---

### Post by Maverick321 on 2008-12-16
You could log into the command prompt and enter this command.

sudo aptitude install ubuntu-desktop

If you have a working net connection, which you should have if you installed it with at net install, this will download and install the ubuntu desktop environment with the default settings.
It may take a while though.

---


---
title: "Dual boot Win XP / Ubuntu eee on Toshiba nb100"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by corto78 on 2008-12-30
Hi to everybody,
i bought a toshiba nb100 (win xp, 1GB RAM, 120Gb HD) and i want to now if it is possible to install also Ubuntu eee, in dual boot manner. Does anyone to give me some feedback in regard?

Tanks...

Tommy78 :)

---

### Post by theinnercityhippy on 2008-12-30
Yes it's absolutely possible.

First things first, you should defragment the disk in XP, which will put all of the fragmented files to the front of the disk.

There are 2 ways to dual boot the computer with Ubuntu and Windows, I will explain the first in more detail as it is I believe the best way to do it. It is also now possible to use a utility called wubi.exe which will install Ubuntu within the windows filesystem, which I believe is not the best way to go about it for reasons too numerous to go into here :-)

I am assuming you have hold of an Ubuntu live CD/DVD, if not then go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Start your system with the CD inserted. If it will not boot from the CD, you need to enter your BIOS (press f2 or esc or something similar during startup) and change the boot order.

When the ubuntu start screen appears, your best option is to "try ubuntu without any change to your computer" (live mode). This way you can check that the finished installation will run on your hardware without any problems. When ubuntu loads there will be an icon on the desktop that says install. Double click on this to start the installer dialog.

Go through the menu items to choose the default language and timezone until you get to the partition editor.

One of the options for this will be to resize hd(0,0) (or whatever your harddisk is called, possibly sda1) and use the freed space. Choose this option and it will automatically shrink the windows partition, create a new partition for Ubuntu and install it there. 

When this is complete, as prompted restart your system without the Cd and you should arrive at a menu which will give you the option of booting Ubuntu or Windows and away you go. Hopefully, as I discovered many moons ago, you will discover that windows has become surplus to requirements, wasting disk space and on it's way off your system with it's tail between it's legs before too long.

Hope this is helpful to you

-JimDog*-

---

### Post by sandman652001 on 2008-12-30
check this post it might help
[http://ubuntuforums.org/showthread.php?t=993133&highlight=toshiba+nb100&page=3](http://ubuntuforums.org/showthread.php?t=993133&highlight=toshiba+nb100&page=3)

---


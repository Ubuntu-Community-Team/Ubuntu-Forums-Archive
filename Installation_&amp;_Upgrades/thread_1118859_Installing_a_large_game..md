---
title: "Installing a large game."
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-07
Suppose I got a 10 GB Linux game and my root or user directory (where the binaries and libraries get installed right?) is only 4 GB.

What do I do in this case?

Cause you cant specify the directory to install it.

---

### Post by kellemes on 2009-04-07
> **dE_logics said:**
> Suppose I got a 10 GB Linux game and my root or user directory (where the binaries and libraries get installed right?) is only 4 GB.

What do I do in this case?

Cause you cant specify the directory to install it.

So you have 10 Gb free somewhere?

---

### Post by dE_logics on 2009-04-07
Yes of course.

But they are all home folder...or manually need to be mounted.

---

### Post by upchucky on 2009-04-07
yes you can install where you want to.

I have all my games on a usb drive, you just need to make sure the game launcher has the location set where the game is

right click the game icon if you have created one, then select properties then select launcher it shows where the game is located and can be changed if you relocate the game. the following example shows guild wars located on my external usb drive "F", and the launcher associated with wine in my home partition

env WINEPREFIX="/home/electric/.wine" wine "F:\Guild Wars\Gw.exe

---

### Post by dE_logics on 2009-04-08
I'm talking about native linux games.

Suppose they came in a deb package...and its 10GB, can then I specify the location.


I know I can specify the location of windows installations through WINE.

---

### Post by dE_logics on 2009-04-08
No solutions?


There's no way the game can be installed in existing space?

How about mounting a partition in one of directories?

---

### Post by upchucky on 2009-04-08
yes, at the command line you tell it where to put the game, then create the links in the launcher to the game.

it is best to set up your home directory on a separate partition anyway, search the site on how to create separate home partition, do that then put games/files there.

---

### Post by dE_logics on 2009-04-09
How do you do that?

What can we specify for the installation?...I mean can we specify where to put the libraries/binaries etc...?

Can gdeb do it?...do we have any other GUI installer to do this...or a commandline alternative?

---

### Post by dE_logics on 2009-04-10
Someone pls?

---

### Post by dE_logics on 2009-04-11
I've not found anything online......

---

### Post by weeman7007 on 2009-04-11
what game is it?

if you have a separate home partition then you could shrink that by a few gigs and then grow the root partition, ideally thy will be right next to each other on the hdd otherwise you will have a long wait while it moves it

---

### Post by dE_logics on 2009-04-11
Ok...I had that idea too.

That means there's no way this can be done.

Also I've seen that the installation of games can be specified to a directory.

---

### Post by 3rdalbum on 2009-04-11
If you're using one of those binary installers ( you know, where you run a script and it opens a window where you can install the game, the script usually has ".sh", ".run" or ".bin" at the end) then you can usually specify the destination directory inside the GUI for the installer.

If you're installing a Debian package (.deb) then you cannot specify a directory - the package itself specifies the directory.

Your option in this case would be to make a new partition or install a new hard disk to hold the contents of /usr, and then mount it at /usr (once it has all the contents of /usr on it, of course!).

A theoretical possibility could be to open the Debian package using Archive Manager (File Roller) and decompressing the "data.tar.gz" to your external hard disk; then create symbolic links (what Windows calls "Shortcuts") on your filesystem to where the actual data is. For instance, if the Debian package was to install a program called "xmoto" into /usr/bin, you would create a link at /usr/bin/xmoto that would be linked to the location of that program on your external hard disk.

That's a little bit of work, but I think it would accomplish what you are looking for.

---

### Post by dE_logics on 2009-04-11
> If you're using one of those binary installers

Yeah I need to encounter that.

Just installed from source codes and deb packages.

Say...java has such sort of installer for x64 Linux.

> Your option in this case would be to make a new partition or install a new hard disk to hold the contents of /usr, and then mount it at /usr (once it has all the contents of /usr on it, of course!).

You mean partition mounted in one of the system folders will be used for additional space?

> A theoretical possibility could be to open the Debian package using Archive Manager (File Roller) and decompressing the "data.tar.gz" to your external hard disk

That means the program was a portable application...right?

---

### Post by dE_logics on 2009-04-11
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch27_:_Expanding_Disk_Capacity](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch27_:_Expanding_Disk_Capacity)


Does this have to do with it?

---


---
title: "Old Windows 95 PC, BIOS does not support boot from CDROM"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by | MM | on 2006-01-11
So basically.  The PC is 11 years old, running a decrepit version of windows 95.  I want to test the LiveCD to ensure things run well enough and assuming all things go well install Ubunut 5.10.  But to do so requires a boot from CDROM.  A function not supported by the particular BIOS/Motherboard in the system.

So i figure i need some sort of bootable floppy that then boots from the CDROM?  I have no idea on how to achieve this.  Howto required :P

Also, the system only has 1.9GB of HD space.  Will Ubuntu fit on the hardrive?

It definately needs the relative usability of Win95, because the people using it are not really all that tech savvy.  So i cant skimp on usability, i need all the default interface elements of Ubuntu.

Other than that all i want is OpenOffice Writer, the OOo Spreadsheet, interface with a Windows network, Print via a windows network and Opera Browser.  Everything else is absolutely superfluous to requirements.

I notice the base install on MY MODERN 80GB system was ~3GB.  So is the Ubuntu installer able to handle the fact that this particularly old PC only has 1.9GB?  So i guess what i am asking is: is there away to install Ubuntu without the apps and massive repositories of functionality that will be unnecessary on this system?


Advice much appreciated.


Also, how is ubuntu gonna run in general terms.  Will the defualt interface be responsive, things like that.  How will OOo preform?  Are there low spec alternatives that can still handle .doc files?

Specifications as far as i can recall:

Pentium 133MHz
HD 1.9GB
Memory ~80MB  (recently upgraded :P)

---

### Post by Qrk on 2006-01-11
OO.o will not perform well. Abiword is less resource intensive and may work slowly, at least. Abiword handles .docs, also.

But you won't be able to get Gnome up on such an old computer. XFCE probably will be too big as well. 

Ubuntu may not be the right distro for that computer. 

Debian still has install floppies; and lets face it, ubuntu without all of the jazz is Debian. [http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)

Puppy is a good choice because it comes preconfigured, and has a desktop environment very similar to windows 95. 

[http://shots.osdir.com/slideshows/slideshow.php?release=492&slide=6&title=puppy+linux+1.0.6+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=492&slide=6&title=puppy+linux+1.0.6+screenshots)
[http://www.goosee.com/puppy/](http://www.goosee.com/puppy/)

It will boot from a zip disk, but no floppies.

---

### Post by adriantry on 2006-01-11
Last week I discovered Vector Linux ([www.vectorlinux.com](www.vectorlinux.com)) which is designed for older computers. It uses IceWM, XFCE and Fluxbox as window managers. The way they set up IceWM is very attractive and very useable.

It has the bonus advantage of not needing to be installed from CD. You can download it into Windows, and run a program to install it from there.

The computer I installed it onto has a Celeron 600 processor, 64 MB RAM and a 20 GB hard drive. It runs very well, and will run well on even lesser computers. I'm very impressed.

Adrian

---

### Post by lha on 2006-01-11
I don't think Gnome on your computer is a good idea. Is Ubuntu right distro for you? Maybe you should give a thought on distros that are designed for older computers. If you still think Ubuntu is the one, I've posted instruction on [using existing Windows install]("http://ubuntuforums.org/showthread.php?p=647002#post647002") to launch the Ubuntu installer. You really should do a server install first and then add a light-weight window-manager with apt-get. To make a server install, change the second line in breezy.bat to
```
loadlin.exe linux vga=normal initrd=initrd.gz base-config/package-selection= base-config/install-language-support=false ramdisk_size=16384 root=/dev/rd/0 rw --
```

---

### Post by az on 2006-01-11
Smart Boot Manager is on the install cd.  It is in the install folder. You rawwrite it to a floppy and then boot it - it detects all your hardware and offers you what it can boot from.  It is made for systems which the bios will bot boot a cdrom.

I would suggest you install a base system with the server option and then install a few packages for a desktop.  You need to log in, enable the universe repository, update and run:

sudo apt-get install x-window-system-core xterm icewm menu abiword mozilla-firefox gdm

---

### Post by ygarl on 2006-01-11
I agree: ICEWM is an excellent choice... Very lightweight and it even looks a lot like Win95

---

### Post by christhemonkey on 2006-01-11
if you defo want ubuntu, then smart boot manager is the way, to go. I have it on a 166mhz ex-95 machine as well! (though with 8gb hd)

---


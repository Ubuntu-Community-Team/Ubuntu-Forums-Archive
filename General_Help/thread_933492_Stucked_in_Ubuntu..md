---
title: "Stucked in Ubuntu."
date: 2008-09-29
forum: General Help
---

### Post by Visias on 2008-09-29
HELP

Im new to ubuntu. And after I reinstalled this wubi nothing works.

I got an error sign saying: "An error occurred, please run PackageManager from the right-click menu or apt-get in a terminal to see what is wrong.
The error messege was: ' Error: Opening the cache
(E:Ecountered a section with no Package:header,E:Problem with MergeList /var/lib/dpkg/status, E:The package list or stadus file could not be parsed or opened.)'Dette betyder som regel at de installerede pakker ikke har alle de pakker de afhænger af installeret" 

I can't use Add/remove programs or Synaptic
And every time I open Synaptic I get the messenge:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: Pakkelisten eller statusfilen kunne ikke åbnes eller forstås.
E: _cache->open() failed, please report.

I cant install anything.. PLEASE HELP !!

---

### Post by fooman on 2008-09-29
try running the following commands in a terminal...*one at a time*:

```
cd /var/lib/dpkg

sudo mv status status-bad

sudo cp status-old status

sudo apt-get update
```

see if that helps.

---

### Post by LowSky on 2008-09-29
or this command ```
sudo dpkg --configure -a
```

---

### Post by Visias on 2008-09-29
**When I uses Foomans types i get this:**

Ignorerer cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ignorerer cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-da
Ignorerer cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-da
Ignorerer cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ignorerer cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ignorerer cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Fejl cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Brug apt-cdrom for at apt kan lære den at kende. apt-get update kan ikke bruges til at tilføje nye cd'er
Fejl cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Brug apt-cdrom for at apt kan lære den at kende. apt-get update kan ikke bruges til at tilføje nye cd'er
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy Release.gpg
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/main Translation-da
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/restricted Translation-da
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/universe Translation-da
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/multiverse Translation-da
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates Release.gpg
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/main Translation-da
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/restricted Translation-da
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/universe Translation-da
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/multiverse Translation-da
Henter:1 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy Release [65,9kB]
Henter:2 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates Release [58,5kB]
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/main Packages 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/restricted Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/main Sources   
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/restricted Sources
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/universe Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/universe Sources
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/multiverse Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/multiverse Sources
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/main Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/restricted Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/main Sources
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/restricted Sources
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/universe Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/universe Sources
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/multiverse Packages
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates/multiverse Sources
Hentede 124kB på 0s (148kB/s)
W: Kunne ikke hente cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz Brug apt-cdrom for at apt kan lære den at kende. apt-get update kan ikke bruges til at tilføje nye cd'er

W: Kunne ikke hente cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz Brug apt-cdrom for at apt kan lære den at kende. apt-get update kan ikke bruges til at tilføje nye cd'er

E: Nogle indeksfiler kunne ikke hentes, de er blevet ignoreret eller de gamle bruges i stedet.
visias@visias-laptop:/var/lib/dpkg$

---

### Post by eZtaR on 2008-09-29
Basically what it states (in Danish) is that it cannot get the index files from the hardy cd? :S

---

### Post by Visias on 2008-09-29
I can now use synaptic .. but add/remove still dosnt work ..

when I open add/remove it says:
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When I updated in synaptic. It didn't work?

---

### Post by heysmithy on 2008-12-18
Im having exactly the same problem.. did anyone ever find a solution for this?

---

### Post by oldos2er on 2008-12-18
Try removing the CD-ROM from your Software Sources. System, Administration, Software Sources.

---

### Post by tiggsy on 2008-12-19
Ok, I have same problem, and it all started with an update to cupsys that didn't work.

I've done all the stuff both Fooman and Lowsky said

from the second one I got this: 

```
dpkg: error processing cupsys (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 cupsys

```

so I tried to uninstall it, but synaptic failed to do this and came up with half an error:

```
E: cupsys: Package is in a very bad inconsistent state - you should
```

the details showing up in Changes applied were: 

```
dpkg: error processing cupsys (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
```

It occurred to me that it may be the gui at fault, so I tried: sudo apt-get remove cupsys in terminal

I got: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  cupsys
0 upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? 
dpkg: error processing cupsys (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

so i did sudo apt-get remove cupsys and got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  cups-pdf cupsys-driver-gutenprint foomatic-filters-ppds hplip xpdf-korean
  xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified
Recommended packages:
  avahi-utils
The following packages will be upgraded:
  cupsys
1 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
Need to get 0B/1863kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 144939 files and directories currently installed.)
Preparing to replace cupsys 1.3.7-1ubuntu3.1 (using .../cupsys_1.3.7-1ubuntu3.2_i386.deb) ...
Ignoring nonregistered document `cupsys'
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
update-rc.d: warning: /etc/rc2.d/S19cupsys is not a symbolic link
invoke-rc.d: not a symlink: /etc/rc2.d/S19cupsys
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So i appear to be stuck up s**t creek without a paddle

---

### Post by stalkingwolf on 2008-12-19
You can try this,
reboot. At the grub menu select Recovery mode.  If you are running Ubuntu
by it self at the grub menu hit ESC then recovery.
After recovery runs you should get a window that offers several options,
normal boot and Fix broken packages among them.

Select fix broken packages. after it is done do a normal reboot.

Hope that helps.

---

### Post by tiggsy on 2008-12-19
Yes! It worked. I now have installed php,mysql,apache and ruby

Then I ran update. It wanted to do cupsys again...

Should I let it? And if not (as it was the cause of the problem in the first place), how do i get it to stop telling me it's available?

---


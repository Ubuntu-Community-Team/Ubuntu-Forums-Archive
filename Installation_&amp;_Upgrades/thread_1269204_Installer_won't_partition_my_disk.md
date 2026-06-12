---
title: "Installer won't partition my disk"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by bigkb0y on 2009-09-17
I am installing Ubuntu 9.04 Desktop on my old laptop using the alternate text based installer because the Live cd won't run. It's an IBM 770X 233Mhz 64MB RAM 8.1Gig HD. I originally booted the laptop into DOS with Windows98 CD and FDISK didn't even recognize a partition so I deleted all partition information, created 1 Primary partition and formatted it FAT32.

The Ubuntu setup seems to run fine at first. It has me chose language, keyboard, detect hardware, enter hostname, time zone, detect disks, start up partitioner and I get this screen:

[IMG]http://i391.photobucket.com/albums/oo360/bigkb0y/UbuntuError.jpg[/IMG]

When I press Continue the menu just disappears and I am left with the blue screen and a white line at the bottom and I can type stuff in but it does nothing.

Is it not detecting my Hard-Drive since it says ??? ???

I've tried using the following boot parameters with no results:
disk=cylynders,heads,sectors (it's an 8100MB IBM HD so I actually used disk=8320,10,512)
generic.all_generic_ide=1
acpi=off
noapic
nolapic

I also tried booting up the computer into DOS with the Win98 cd again but it just goes to a black screen with a down arrow character and a flashing _ character.

---

### Post by Partyboi2 on 2009-09-18
Hi, having 64 mb of ram is not going to be enough to use Ubuntu, (requires 256mb) you may need to look at some other distros like [[COLOR=Blue]dsl[/COLOR]]("http://www.damnsmalllinux.org/") (Darn Small Linux) which runs on low spec machines.

---

### Post by bigkb0y on 2009-09-18
Hmmm the Ubuntu Desktop overview website says:

**System requirements **

 [LEFT] Ubuntu is available for PC, 64-Bit PC and Intel-based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. [/LEFT]

Reference: [http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)



Looking further into the site it says this:
**Desktop installation**

 Most people will want to install a desktop system such as **Ubuntu**, **Kubuntu**, or **Xubuntu**. A desktop system is typically used for personal computing tasks and has a graphical user interface. 
 
**Bare Minimum requirements**

 It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the *Alternate install CD* to attempt such an installation. 

[LIST]
[*]300 MHz x86 processor 
[*]64 MB of system memory (RAM) 
[*]At least 4 GB of disk space (for full installation and swap space) 
[*]VGA graphics card capable of 640x480 resolution 
[*]CD-ROM drive or network card
[/LIST]

Reference: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)


So how is the bare minimum system memory requirement 64MB whenever the CD requires 256MB?

---

### Post by QIII on 2009-09-18
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Partyboi2 on 2009-09-18
>  So how is the bare minimum system memory requirement 64MB whenever the CD requires 256MB?
The minimal install is  a barebones install with no Deskop gui, windows manager etc. That is why the memory requirements are lower.
The Desktop version comes with a Desktop Gui, Windows manager etc..

---

### Post by bigkb0y on 2009-09-18
I see. I definately need a GUI so I think I am going to try Damn Small Linux.

Do any of you suggest any other compact versions of Linux?

---

### Post by QIII on 2009-09-18
I had DSL on an ancient laptop and I liked it there.  You'll definitely take a hit on ease of application installation.

You could also try PuppyLinux.

Give this a look:

[http://distrowatch.com/](http://distrowatch.com/)

There is a search page, where you can select "old computers"

---


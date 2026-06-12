---
title: "Install problems on Averatec 3200"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by msfisher on 2009-06-14
I'm a near-newbie.  I have an aging Averatec 3200 which I've tried to load Linux on for a couple of years.  Honestly, I've tried a lot -- Ubuntu since v.7; Fedora 9, 10 & now 11; Mandriva 2007 thru 2009, Free and One; OpenSuSE since 10.2; Foresight; PCLinuxOS (newest); OpenSolaris (I know, UNIX, not Linux, plus it trashed my MBR!); Debian (newest core install); Simply Mepis 6, 7 & 8; Linux Mint 4 thru 7 and Zenwalk 6.

Only one of these installed successfully -- Linux Mint 4, and it was crippled by not recognizing either the Broadcom wireless or the VIA wired NIC.  I know, I could have used ndiswrapper, but at the time I was enough of a newbie to try anything else first.

Just now, I tried Fedora 11.  In contrast to some of the installers, it actually got through partitioning and started to install files.  

Open SuSE does much the same thing.  So does Debian.  

When I try to load Ubuntu, it gives me lots of errors (especially for the wireless NIC) then defaults to the command line.  Running startx I find that there are no valid modes and though a screen is found it has no usable configuration.  I tried the "safe video" option and got the same result.  The Alternate Install CD does install, but I get the same errors on reboot and end up at the CLI.

Mandriva barely gets past the first installation screen.

Foresight doesn’t even start.

I got PCLinuxOS to load live using VESA rather than X but couldn’t get it to install.  

Even using “safe” graphics, Zenwalk 6.0 installer starts but tells me that X11 won’t run.

Here are the particulars of the laptop:

Mainboard:	Averatec 3200
Chipset:	VIA KM400
Processor:	AMD Athlon XP-M @ 1533.3MHz
Memory:	        1024MB
Video:		VT82C570 MV IDE Controller KM400 Graphics Adapter
Network Card :  Broadcom Corp BCM4306 802.11g Wireless NIC
Network Card :  VT82C570 MV IDE Controller VT6102 Rhine II Fast Ethernet 

I have the 40gig drive partitioned into ~20gigs for Windows XP Home and the rest for Linux with a 2gig swap partition.

Anyone have any ideas about loading ANY Linux distro on this thing (I prefer Ubuntu)?

---

### Post by quixote on 2009-06-14
Nobody who's installed that many linuxen can be called a newbie! :D

Ubuntu has been installed on Averatecs ([https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)) but I don't see your specific model there.  Sounds like others had the same general problems getting X to work  :(.  Maybe if you could contact some of those users they'd have some useful ideas?

This might be one of those things where the best use of your time is to donate the laptop to a school and move on??  I'm sure it's a soluble problem if you can figure out exactly how to customize xorg.conf, but is it worth the effort?

---

### Post by hackersdbm on 2009-07-21
Dude I've the same laptop with the same problem installing Ubuntu 8.10. I already figure out how resolve this issue in a forum  

[http://ubuntuforums.org/showthread.php?p=7226784](http://ubuntuforums.org/showthread.php?p=7226784)   

may be you can do the same same on Fedora. Out there are so many people having the same problem with that laptop's serie.  Perhaps the wireless is begging slowly, so you need to resolve 2 issue instead 1. I've ubuntu 8.10 installed already in my averatec 3200 series but the wireless is still slow. So Good lock with FEDORA 11

Sorry my bad English 

sorry 
:)

---


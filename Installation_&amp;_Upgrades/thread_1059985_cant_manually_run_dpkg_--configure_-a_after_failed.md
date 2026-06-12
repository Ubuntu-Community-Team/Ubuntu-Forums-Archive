---
title: "cant manually run dpkg --configure -a after failed install or upgrade"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Asmund on 2009-02-04
Can someone please help?

Im a bit new to linux, but apparently "the package libxine1-bin 1.1.15-0ubuntu3.1 failed to install or upgrade", and now whenever I try to run apt-get, or add/remove it tells me to manually run dpkg --configure -a. 

However, when I run that in the terminal I only get:
```
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```

Running sudo apt-get -f install gives me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing libxine1-bin (--configure):
 package libxine1-bin is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

Allthough to be completly honest, Im not even sure what this command is supposed to do, I only ran it because thats what some other user on the forum with simular problems was told to try.. I know, I know... Im such a noob.. 

Ive been reading threw posts on the forum and tried running sudo dpkg -l | grep -v ^ii  to get a list of faulty packages, which I could then remove, but that brings up: 

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-============================================

iF  gxine                                      0.5.903-2ubuntu2                        the xine video player, GTK+/Gnome user inter
rc  libavcodec51                               3:0.svn20080206-12ubuntu3               ffmpeg codec library
iU  libxine1                                   1.1.15-0ubuntu3.1                       the xine video/media player library, meta-pa
iW  libxine1-bin                               1.1.15-0ubuntu3.1                       the xine video/media player library, binary 
iU  libxine1-console                           1.1.15-0ubuntu3.1                       libaa/libcaca/framebuffer/directfb related p
iU  libxine1-ffmpeg                            1.1.15-0ubuntu3.1                       MPEG-related plugins for libxine1
iU  libxine1-misc-plugins                      1.1.15-0ubuntu3.1                       Input, audio output and post plugins for lib
iU  libxine1-x                                 1.1.15-0ubuntu3.1                       X desktop video output plugins for libxine1
rc  myspell-en-us                              1:2.4.0-2ubuntu4                        English_american dictionary for myspell

```

Are any of these working in any way, or will removing them affect my system in a bad way? Im really at a loss here, so any help would be very appreciated!

---

### Post by Hooya on 2009-02-04
Try using Synaptic to completely remove (Purge) the offending programs.  Then do a reload in synaptic.  If those programs are dependencies, install the programs they depend upon if you need those programs back.  Otherwise, just leave it alone.

You can also try "dpkg --remove" on the offending packages, which I think does the same thing.

By the way, "apt-get -f" attempts to "correct a system with broken dependencies in place.  This option, when used with install/remove can omit any packages to permit APT to deduce a likely solution."  It's another way to attempt to reinstall broken programs, similar to the dpkg --reconfigure command you first tried.

---

### Post by Asmund on 2009-02-05
Thanks! I completely removed all of them using synaptic, and now everything seems to work again. :) Really appreciate it! Big thank you from Norway!

---


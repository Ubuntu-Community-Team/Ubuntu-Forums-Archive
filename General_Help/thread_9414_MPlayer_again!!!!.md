---
title: "MPlayer again!!!!"
date: 2004-12-28
forum: General Help
---

### Post by paradox on 2004-12-28
HI!

I installed mplayer-common but i have this error message:

CPU: Advanced Micro Devices Athlon MP/XP/XP-M Barton 2191 MHz (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


yes, mplayer common is compiled for Pentium4!!! So, i try to install mplayer-586 but i see this message in apt-get:

The following packages have unmet dependencies:
  mplayer-586: Depends: libartsc0 (>= 1.3.1) but 1.2.3-1 is to be installed
               Depends: libggi2 (>= 1:2.0.5) but 1:2.0.4-3 is to be installed
               Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7 is to be installed
               Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is to be installed
E: Broken packages


GHGHGHGHGHGH....i must compile mplayer to sources?

Any idea?!?!?

---

### Post by diebels on 2004-12-28
try "testing main" instead of "unstable main" for a bit older packages?

---

### Post by paradox on 2004-12-28
ma sources.list is:

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by paradox on 2004-12-28
I  must add another repository?

---

### Post by lameaim on 2004-12-28
[QUOTE=paradox]I  must add another repository?[/QUOTE]
Try installing mplayer-686

---

### Post by paradox on 2004-12-28
Seems to be apt-get try to install requested packages but he don't found updated version in repository...

---

### Post by paradox on 2004-12-28
[QUOTE=lameaim]Try installing mplayer-686[/QUOTE]

humm....still don't work:

 mplayer-686: Depends: mplayer-586 but it is not going to be installed

---

### Post by Quest-Master on 2004-12-28
Don't install MPlayer from apt-get. Now, you need to remove all of the packages relating to MPlayer through Synaptic. Then, install MPlayer from source. Best way to do it.

---

### Post by paradox on 2004-12-28
[QUOTE=Quest-Master]Don't install MPlayer from apt-get. Now, you need to remove all of the packages relating to MPlayer through Synaptic. Then, install MPlayer from source. Best way to do it.[/QUOTE]

Fortunatly i have installed only requested base packages:

libavcodec2 libfaad2-0 libggi2 libgii0 libgii0-target-x libimlib2 liblame0 libpostproc0 libsvga1 libxvidcore4 mplayer-custom

I uninstall with apt-get all package (one by one...exept imlib2: i used it for enlightenment :D), is correct?

Anyway i cannot install mplayer from source...x-system-dev is too big for my line-phone :(( In other install mplayer for sources don't cause upgrade problem in future (isn't a package...)? This is strange: don't exist a secure method and packages for install without problems Mplayer under machines NON Pentium...Is Mplayer not a kernel :D

I can install Xine?!?!? I try apt-get install xine but the package isn't found...

---


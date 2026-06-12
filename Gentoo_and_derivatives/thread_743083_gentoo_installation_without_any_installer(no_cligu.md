---
title: "gentoo installation without any installer(no cli/gui)"
date: 2008-04-02
forum: Gentoo and derivatives
---

### Post by deepclutch on 2008-04-02
hi,
I have to install gentoo this week.I had installed gentoo lastly on jan 2006 or so(had used from 2004 ).
now this installer thing is making me crazy :confused: as I read that these installers are buggy.

I want to install the old way.ie,copy extract stage3(from funtoo) ,portage,chroot  .

I'd like to hear the guidelines from the experts here:guitar:
what I want with gentoo is,a optimized fast Gnome Desktop without much features like bluez,server support etc .
I want to completely disable "qt" via USE flag.
Can someone help me what should I put in USE flag.

also my pc is a old prescott 2.8Ghz HT,915GV mobo,7300GT(nvidia) 256MB dedicated,384MB DDR-I RAM.
will someone share their /etc/make.conf of same configuration?

BTW,gentoo 2008_beta livecd is released?

Thank You :)

---

### Post by Gen2ly on 2008-04-02
the gentoo min cd has always been stable, might give that a try otherwise they should be testing a new install cd soon.

---

### Post by regomodo on 2008-04-03
> **deepclutch said:**
> :
what I want with gentoo is,a optimized fast Gnome Desktop without much features like bluez,server support etc .
I want to completely disable "qt" via USE flag.
Can someone help me what should I put in USE flag.


Put in /etc/make.conf

USE="-kde =qt3 -qt4" among others

---

### Post by deepclutch on 2008-04-05
One more query:
How to use genkernel to compile a custom kernel with initramfs support and initramfs.img generated?
(dont want **initrd** though!)
also how to use ccache while emerging packages? :?

...and here is my /etc/make.conf  :D :
```

# These settings were set by the catalyst build script that automatically 
# built this stage. 
# Please consult /etc/make.conf.example for a more detailed example. 
#CFLAGS="-O2 -march=i686 -pipe" 
CFLAGS="-march=prescott -O2 -pipe -fomit-frame-pointer" 
#CXXFLAGS="-O2 -march=i686 -pipe" 
CXXFLAGS="${CFLAGS}" 
# This should not be changed unless you know exactly what you are doing.  You 
# should probably be using a different stage, instead. 
# WARNING: Changing your CHOST is not something that should be done lightly. 
# Please consult http://www.gentoo.org/doc/en/change-chost.xml before changing it. 
CHOST="i686-pc-linux-gnu" 
 
MAKEOPTS="-j3" 
 
USE="bash-completion fontconfig gtk gpm gnome firefox hal lm_sensors nptl truetype xscreensaver xv xcomposite opengl aiglx win32codecs -arts -kde -qt3 -qt4 " 
 
AUTOCLEAN="yes" 
 
PORTAGE_TMPFS="/dev/shm" 
 
FEATURES="ccache" 
 
GENTOO_MIRRORS="ftp://ftp.gtlib.gatech.edu/pub/gentoo/ ftp://de-mirror.org/distro/gentoo/  ftp://ftp.kaist.ac.kr/gentoo/" 
 
CCACHE_DIR="/var/tmp/ccache" 
CCACHE_SIZE="2G" 

```

---

### Post by Gen2ly on 2008-04-06
flags look pretty good, nothing too radical.   Keep in mind you can use \ and return to make reading easier, for example:

```
USE="gnome firefox \
     -kde -art"
```

and the cache looks just fine.  There's an entry at the Gentoo wiki that can tell how to test it.

---

### Post by deepclutch on 2008-04-06
^thanks! will use "\" ;) 
also do I want to use GRP?I mean building binary as a option?Can we live without that option :?

also what about masked packages?Will it be needed to merge gnome-2.22 in full :)

Thanks again!

---

### Post by Gen2ly on 2008-04-06
Building binaries is what portage does.  It grabs souce code and compiles it into executable code the computer understands.  There is an option that can be put in the make.conf the saves all binaries to they can be easily (and quickly) re-installed.  Personally, I don't use this but some do.

There are some masked packages in portage but for the most part nothing real important.  Gnome 2.22 was masked for testing but no longer is.

---

### Post by deepclutch on 2008-04-07
Thanks! :)
yeah,I think it is a wastage of space to build binaries :?:

---

### Post by deepclutch on 2008-04-11
I have the "SYNC=repo" line in /etc/make.conf .my installation is resting for a week or so :p .
now,
I have a custom compiled kernel using genkernel(--menuconfig) .

Now,how to install Gnome-2.22 please?
Is Gnome-2.22 available on main repository?
also emerge gnome-lite will install which version of Gnome? :?

and Do I have to use portage overlay/using layman to install Gnome?
and here is my /etc/make.conf :)
```

# These settings were set by the catalyst build script that automatically
# built this stage.
# Please consult /etc/make.conf.example for a more detailed example.
#CFLAGS="-O2 -march=i686 -pipe"
CFLAGS="-march=prescott -O2 -pipe -fomit-frame-pointer"
#CXXFLAGS="-O2 -march=i686 -pipe"
CXXFLAGS="${CFLAGS}"
# WARNING: Changing your CHOST is not something that should be done lightly.
# Please consult http://www.gentoo.org/doc/en/change-chost.xml before changing.
CHOST="i686-pc-linux-gnu"
USE="a52 acpi aiglx alsa bzip2 bash-completion chroot cpudetection dbus dvd fontconfig gtk gpm gnome gstreamer firefox hal hddtemp lm_sensors mp3 mp4 mpeg mpeg2 mplayer nls nptl truetype xscreensaver xv xvid xcomposite xine opengl aiglx mime ogg theora symlink win32codecs -arts -cups -beagle -kde -mono -networkmanager -oss -pcmcia -qt3 -qt4 "

MAKEOPTS="-j3"

AUTOCLEAN="yes"

PORTAGE_TMPFS="/dev/shm"

FEATURES="sandbox ccache parallel-fetch"

GENTOO_MIRRORS="ftp://gentoo.kems.net/mirrors/gentoo/ ftp://ftp.gtlib.gatech.edu/pub/gentoo/ http://distfiles.gentoo.org"

CCACHE_DIR="/var/tmp/ccache"
CCACHE_SIZE="2G"
ACCEPT_KEYWORDS="x86"
VIDEO_CARDS="nvidia vesa"
INPUT_DEVICES="mouse keyboard"
EMERGE_DEFAULT_OPTS="--ask --verbose"

```

---

### Post by Gen2ly on 2008-04-11
Ah good most of the basics are done.  If wanting to install Gnome 2.22 it will have to be unmasked.  There's an upgrade to Gnome-2.22 guide on the gentoo.org website in the docs section.  Also I wrote about it on my blog if it helps.

---

### Post by deepclutch on 2008-04-11
well,Thanks, and I am now reading ur blog post ;)

---


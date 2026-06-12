---
title: "X not starting on Eee PC"
date: 2008-08-08
forum: Hardware
---

### Post by xelapond on 2008-08-08
Hey everyone, 

I am going out of town tomorrow, and I really need my laptop to work.  I'm not really worrying at all, you guys are great about quick help, but here is dilemma:

I have an Eee PC 2G Surf, which earlier today I tried to load eeeXubuntu because I don't like the Xandros they put on it.  It installed fine, no errors or anything, but X won't start.  I followed this guide [here]("http://forum.eeeuser.com/viewtopic.php?id=11651"), my SD card is an 8 gig which has 4 gigs of /usr on it, 512 megs of swap, and 3 gigs of /media/data.

It brings to me a shell, so I log in.  After login I type startx, and get the following output:
```

xauth:  creating new authority file /home/granny/.serverauth.5662


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Vesto 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  8 18:45:16 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
(EE) AIGLX error: dlopen of /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
Atom 4, CARD32 4, unsigned long 4
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Synaptics DeviceOff called
(EE) intel(0): I830 Vblank Pipe Setup Failed 0

waiting for X server to shut down (EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.




```

All help is appriciated, 

Alex

---

### Post by starcannon on 2008-08-09
I have a 2g, and heres what I ended up doing... don't shoot me its gonna require some hours tonight if you have to leave tomorrow.

Install Puppeee linux, its the best thing that ever happened to the 2g Surf.

Before I found Puppeee I had written the 2g off as $200 wasted, now I use it regularly. No problems, all the modules are already there, no scripts to run, no hassels. The interface is lite, basic, and very functional. You'll have a 2g thats as snappy as a 900, and the whole os installs on just a few hundred megabytes leaving aournd 1.5gb of free space for... mp3's of course :)

GL thats the best I can do with this very limited piece of hardware.

---

### Post by xelapond on 2008-08-12
I have never tried Puppy Linux, but I will give it a try.  I already left, I got X to start by running xinit instead of startx.  No idea why.  Now libglib is messed up, so no GUI programs work, but I can do pretty much everything in emacs-nox.

I will definitely try Puppy when I get home.

Thanks!

Alex

---

### Post by starcannon on 2008-08-12
Heres some links for you:

Download the ISO (its so tiny hehe)
[http://waltonpond.com/eeepc/2008-3-16/pupeee-b4.iso](http://waltonpond.com/eeepc/2008-3-16/pupeee-b4.iso)

View the "official thread"
[http://www.murga-linux.com/puppy/viewtopic.php?t=25896](http://www.murga-linux.com/puppy/viewtopic.php?t=25896)

View the Wiki
[http://puppylinux.org/wiki/archives/old-wikka-wikki/everything-else/pupeee](http://puppylinux.org/wiki/archives/old-wikka-wikki/everything-else/pupeee)

I was amazed at what it did for my 2g, made it into a very respectable umpc.

---

### Post by RedPandaFox on 2008-08-12
I get the same problem on my 2gb surf. No idea why, I honestly think the 2gb doesn't like Linux, at least mine doesn't. Every time I put Linux on it, Ubuntu, EeePCLinuxOS, EeeXUbuntu, Xandros, Puppeee, it always has a problem, Yet, when I put on EeeXP, it works fine. Weird.
Also whenever I install to the SD card, it ALWAYS have a problem with X.
I'm running off a 160Gb external USB HDD atm with Ubuntu 8.10 Alpha installed, running very well i must say, The only problem is it doesn't fully shut down, and the screen flashes red when I attempt to shutdown.

---

### Post by starcannon on 2008-08-12
The shutdown issue is connected to the sound in most cases, the work around is:

[http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy](http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy)

that will more than likely fix that issue for you.

GL and have fun

---

### Post by RedPandaFox on 2008-08-12
> **starcannon said:**
> The shutdown issue is connected to the sound in most cases, the work around is:

[http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy](http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy)

that will more than likely fix that issue for you.

GL and have fun

No help :( Still got the light on and still got red flashing.

---

### Post by starcannon on 2008-08-12
Shutdown, pull the battery, wait say 15-30 seconds, pop battery back in, and try shutdown again. I know that the acpi on our eee's has not been fully supported yet, I'm not sure if that will clear it for you, but it does clear a fan that refuses to throttle down.

---


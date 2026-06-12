---
title: "Lucid Lynx + ATI Mobility Radeon 9600 + fglrx?"
date: 2010-05-25
forum: Hardware
---

### Post by BlueInkAlchemist on 2010-05-25
Greetings, programs!

I've had a [couple]("http://ubuntuforums.org/showthread.php?t=1488387") [issues]("http://ubuntuforums.org/showthread.php?t=1489581") that, for the most part, seem to be resolved.  My system, a Dell Inspiron 8600, is running Ubuntu and I recently stepped up to 10.04, installed Wine 1.2-rc1 & even got World of Warcraft running on it.  There are a couple of bugs and some frame rate issues, and I was wondering if the proprietary ATI drivers (the infamous fglrx) might resolve them if... IF... I can get them working properly.

Here's some pertinent information that might help, the first bit from glxinfo:

```

name of display: :0.0

display: :0  screen: 0

direct rendering: Yes

server glx vendor string: SGI

server glx version string: 1.2

client glx vendor string: Mesa Project and SGI

client glx version string: 1.4

GLX version: 1.2

OpenGL vendor string: DRI R300 Project

OpenGL renderer string: Mesa DRI R300 (RV350 4E50) 20090101 x86/MMX/SSE2 TCL DRI2

OpenGL version string: 1.5 Mesa 7.7.1

```

```
~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

No, I don't *actually* run Compiz on my system, as Lucid's default desktop manager is just fine for me right now, but it's really handy to check my system's information and ensure it's rendering properly.

[Legace]("http://ubuntuforums.org/member.php?u=310401") posted [this handy guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") to installing fglrx and it looks like it'd work for the legacy version I need to install, since ATI no longer supports the 9600 in their current builds.  But before I take the plunge, I thought I'd test the waters by asking:

Is this a smart thing to do?  Should I just be content that WoW runs at all?  If I install fglrx and it works about as well as it did when I first began this endeavour (i.e. not at all) will it be as difficult as I found it before to reinstall radeon?

Thanks in advance for your help and advice.  It's truly appreciated by a still-somewhat novice-level Linux user like myself.  

Looking forward to your replies...  :popcorn:

---

### Post by BlueInkAlchemist on 2010-05-26
Bump!

Any thoughts on the above?  Anything at all?

---

### Post by Nerevar144 on 2010-08-04
> **BlueInkAlchemist said:**
> 
Is this a smart thing to do?  Should I just be content that WoW runs at all?  :popcorn:

Answer:  Probably not a smart thing to do, and yes just be content that WoW runs at all.  I suggest dual booting windows for gaming as of yet on this system, it's too anemic to run any native windows games in wine well.

I'm writing this on the same laptop as yours with the same video card.  I was hoping that I could find a way to speed up the video myself (full screen Flash videos are sloooow and torn), but the more research I do the more I find that it's not going to be a smart move.  That guide you posted a link for is for Hardy... not Lucid.  It will not work.  Besides that, the latest ATI drivers WILL NOT WORK with the RV350 chipset.  It's LEGACY.  If you really want to try the proprietary drivers I suggest you install Hardy, as that's the last release that supports the last version of ATI's drivers that work with the RV350 before they moved it to Legacy status.  I believe it's catalyst 9.3.  The latest ones in the ubuntu repo are 10.7 which simply will not work.
 
Also, someone correct me if i'm wrong but you can't get the 9.3 ATI drivers do work in Lucid because they don't support the version of X.org that Lucid runs.

The route I'm taking is to be happy that the open source MESA driver has 3D accel for this card finally (albeit it's kinda slow) and wait for improvements down the line.  The way I see it is from here on out if you're running Ubuntu's newest releases you're going to be using the open source driver weather you want to or not with legacy ATI cards.

I wish this notebook had an nVidia card....

If you want to game,  dual boot XP.

If you find a way to run ATI's drivers on Lucid, or any tricks to speed up the video, let me know.  I'll do the same.:D

---


---
title: "lockup on logout (ATI X700 Radeon Mobility using fglrx drivers)"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by tbranham on 2007-02-24
Howdy all,

I've searched the forums for several days now, but no solution seems to present itself. I'm trying to install Ubuntu on my girlfriend's laptop (an Acer TravelMate 4400), and I'm having a terrible time getting the video drivers to work with the Radeon Mobility X700 (I know, you're shocked). Anyway, after many hours of work, I've finally got the fglrx drivers working. I get decent framerates in glxgears, etc.

Now, I've got a new, and far more troubling problem. Every time I try to logout, switch users, restart Xorg, switch to another virtual terminal, or shutdown the system, gnome will shut down, then I get a screen full of garbage and a nice system-wide freeze, which requires a hard-reset to remedy. Yuck.

The thing I keep noticing is the look of the framebuffer boot splash -- frankly, it looks terrible, like it's not playing nice with the drivers. I keep thinking that when Xorg is being reset, it isn't playing nice with the framebuffer driver either.

I don't seem to get any kind of errors in Xorg.0.log. Anyway, here's what I've tried:

1) re-install fglrx. No change.

2) re-install Ubuntu. No change.

3) live-cd boot. No change.

4) recovery-mode boot. Seems to work (I can logout without crashing the laptop).

Here is some of the pertinent info:

from xorg.conf
```

...
Section "Module"
        Load  "ddc"
        Load  "vbe"
        Load  "GLcore"
        Load  "dbe"
        Load  "dri"
        Load  "extmod"
        Load  "glx"
        Load  "bitmap"
        #Load  "speedo"
        Load  "type1"
        Load  "freetype"
        Load  "record"
EndSection
...
Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        #Option     "UseInternalAGPGART" "No"
        BusID       "PCI:1:0:0"
EndSection
...
Section "Screen"
        Identifier "aticonfig Screen 0"
        Device     "ATI Graphics Adapter 0"
        Monitor    "aticonfig Monitor 0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option "AIGLX" "off"
EndSection

```

fglrxinfo:
```

sara@amethyst:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

```

sara@amethyst:~$ uname -a
Linux amethyst 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

```

Need anything else? Any hints?

---

### Post by kolach on 2007-02-26
Hi, tbranham!

I'm having exactly the same problem and all the things like "screen full of garbage..."

Radeon Mobility X700 ( on my Acer Aspire 5014WLMi )
fglrx driver

and the same result :( lockup on logout 

HEEEEEEEEEEEEEEEEY anybody help us!!!!!!!!!!!!!!!

---

### Post by cucisan on 2007-02-26
have you tried to use the opensource driver "radeon" which supports cards up to X850?
just as a workaround ... ATI binary drivers can be horrible..
or try another driver version

---

### Post by tbranham on 2007-02-26
cucisan: I gave that a shot last night -- no dice. No matter what driver I'm using in xorg, she locks-up on me when I kill the X server in any way. What a pain!

kolach: Interestingly, I removed the "quiet" and "splash" entries from grub's menu.lst last night, and it seems to cure the lockup. I'm sure my girlfriend can live without a fancy boot splash (we never used it on slack), but it still would be nice to figure out what's going on. Any framebuffer driver experts out there who can offer some advice? Is it possible to get the boot splash to use a different framebuffer driver?

Perhaps the real solution is not to buy a laptop with an ATI graphics chip. Oops, too late.

Thanks!

---

### Post by kolach on 2007-02-26
Great advice, tbranham!!!
I removed only splash keyword and it worked :)))

I've also found one link about this problem, no solution though :(
[http://wiki.cchtml.com/index.php/Troubleshooting]("http://wiki.cchtml.com/index.php/Troubleshooting")
The problem is not new..

Yes, no ati-video based notebooks any more!
(bcm43xx based wifi cards also sucks :)

To cucisan:
One time I've tried radeon driver but couldn't set up 1280x800 resolution
But it must have been my lack of knowledge.

---

### Post by cocoia on 2007-02-26
It's very, very strange that this problem is presenting itself with almost every mobile ATI I have come across. Horrible colored ragged lines on startup , etc.

Do you still have a lock-up when you stop X? How is the issue now that it starts GDM?

---

### Post by tbranham on 2007-02-26
cocoia: Yes, it is strange. Actually, the boot splash in gentoo looked fine (no distortion or terrible colors), but the logout problem was still there. I believe I was using the radeonfb in gentoo, but it seems that Ubuntu is defaulting to vesafb (that's the only module loaded anyway). Nevertheless, there is something strange going on. (incidentally, gentoo ran like crap on that machine. I decided, since I had such good luck installing Ubuntu on *my* lappy, it might fix some of the pesky hardware problems. Whoops.)

kolach: I'm glad it worked for you too. It's not ideal, but it prevents a hard-reset every time you want to shut your system down. I'll just change the default console font (so I can fit a little more text on the screen) and call it good. I'm not holding out too much hope for a better solution -- she'll just have to live with it. (shhhh, I don't want her to find out I said that ;))

---

### Post by cocoia on 2007-02-26
If you'd be very inclined to help her, (and I mean VERY inclined), then you can build a recent  kernel with menuconfig, and select Radeon as builtin. 

That, with some flags, may help. Alas, that's all I can think of. I am trying it myself since I also have little control over other hardware on my laptop.

---


---
title: "Problems with nvidia video card"
date: 2011-09-13
forum: Hardware
---

### Post by Bakuriu on 2011-09-13
Hello, I'm having some troubles with my nvidia drivers.
I'm using kubuntu 11.04 on an Acer Aspire 5742G. The Graphic Card is an nVidia GeForce GT 540M and uses Optimus.

I'm quite new to managing this kind of things, so please be clear with your answers.

First of all here is the report of nvidia-bug-report.sh, even if i don't see anything strange here:
```

giacomo@Giacomo-PC:~$ cat nvidia-bug-report.log
____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see www.nvnews.net) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 9611234

Date: mar 13 set 2011, 23.11.55, CEST
uname: Linux Giacomo-PC 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

The proprietary drivers are installed but not active, or at least this is what "jockey" says.
If i run nvidia-xconfig the generated xorf.conf file prevents X from starting.

I've tried to search for any solution on this forum and on the net, but i found only really old threads(2003/2004) in which a solution was explained. This solution involved modifying an XF86Config(or XF86Config-4) file, but there is no such file on my computer.

I've found out that nvidia-173 and nvidia-96 drivers are blacklisted:
```

giacomo@Giacomo-PC:~$ cat /etc/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```

I've tried to remove the last line, just to see if something would change but i can't see any changes.

From the system log viewer i can see that the GLX extension fails to load:
```

    [    18.902] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

This is the output of glxinfo:

```

giacomo@Giacomo-PC:~$ glxinfo
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

```


also i can't see GLX in the extension avaiable running xdpyinfo:

```

giacomo@Giacomo-PC:~$ xdpyinfo
[...]
number of extensions:    27
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    Generic Event Extension
    GestureExtension
    MIT-SCREEN-SAVER
    MIT-SHM
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    XVideo-MotionCompensation


```

if i'm not wrong there should be GLX and NVIDIA-GLX extensions if the drivers worked fine.

One last detail, the xorg.conf file i'm using right now:
```

giacomo@Giacomo-PC:~$ cat /etc/X11/xorg.conf

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection


```

If i add: Driver "nvidia" to xorg.conf, X wont start.


Given this details, is there anything i can do to have the nvidia drivers work properly?
If they wont work no matter what, does this bug affects other (k)ubuntu versions as well?
I was thinking of trying lucid, but i don't know whether i will have the same problem or not.

Thank you in advance for your help and patience.

---


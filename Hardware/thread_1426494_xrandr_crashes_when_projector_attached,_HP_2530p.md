---
title: "xrandr crashes when projector attached, HP 2530p"
date: 2010-03-10
forum: Hardware
---

### Post by jwe080 on 2010-03-10
I'm running Ubuntu 9.10 (2.6.31), x86_64,  on an HP Elitebook 2530p laptop (with integrated intel mobile 4 graphics controller). 



 I'm trying to connect to an external projector but the system crashes.


 Some external monitors are configured automatically and work well/decently when plugged in but a connected projector (and maybe other monitors?) isn't. To reproduce, after I've turned off visual effects, I plug in the projector, run xrandr -q, and the system freezes up with the keyboard, and mouse unresponsive. Plugging in the projector before booting up causes a kernel panic.  If the visual effects aren't turned off I think plugging in the projector causes an immediate crash.



 How can I configure the settings so that the projector will work (or at least quit gdm without a reboot after this has happened)?
 

Thanks.

---

### Post by f03el on 2010-04-13
Same for me, both the total freeze on "xrandr -q" with the projector plugged in, and the kernel panic upon booting with it plugged in. The projector is an HP mp2220. I have kernel 2.6.31-20-generic and xdpyinfo gives```
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10604000
X.Org version: 1.6.4
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3e00004, revert to Parent
number of extensions:    27
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
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
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1680x1050 pixels (331x207 millimeters)
  resolution:    129x129 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x105
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7a802c
    ButtonPressMask          ButtonReleaseMask        LeaveWindowMask          
    ExposureMask             StructureNotifyMask      SubstructureNotifyMask   
    SubstructureRedirectMask FocusChangeMask          PropertyChangeMask       
  number of visuals:    72
...
```

---

### Post by f03el on 2010-04-14
Now it works for me! I found that the maximum screen size was 8192 x 8192, so I started to suspect that this was too much for the projector. On [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") I found the following lines to add to /etc/X11/xorg.conf, but exactly what made it working needs to be examined further.```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3600 1200
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

---

### Post by f03el on 2010-06-11
I celebrated a bit too early, because soon I got freezes again. The problem is rather a bug in the kernel: [[i965gme] Freezes when attempting to switch to projector (or just detect them)]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/500999")

Sorry if I mislead somebody. The positive is that the bug is found and it seems like it has been fixed in the kernel coming with Lucid (from reading the comments in Launchpad - I haven't tried it myself yet). However, I'm gonna try the [Karmic quick fix]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/500999/comments/25") right away...

---


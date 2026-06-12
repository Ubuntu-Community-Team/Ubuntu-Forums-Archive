---
title: "Resolution Problems with Acer Aspire with Intel Arrandale"
date: 2010-02-07
forum: Hardware
---

### Post by Rayston on 2010-02-07
I have a brand new Acer Aspire 5740-5513 and I installed Ubuntu 9.10 and the first thing I am having an issue with is that I cannot set the resolution above 800 x 600. I should be able to set it to 1388 x 768.

I am pretty sure I have to edit my xorg.conf in some way to fix the problem but I do not know how. Please help.

Here is my xorg.conf is

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

when I run lspci I get

00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 12)

when I run

lspci -v -s 00:02.0

I get the following

00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 12)
Subsystem: Acer Incorporated [ALI] Device 033e
Flags: bus master, fast devsel, latency 0, IRQ 31
Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
Memory at d0000000 (64-bit, prefetchable) [size=256M]
I/O ports at 1800 [size=8]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

here is my info from xrandr

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
800x600 61.0*
640x480 60.0

here is my info from xpdyinfo











number of supported pixmap formats: 7
supported pixmap formats:
depth 1, bits_per_pixel 1, scanline_pad 32
depth 4, bits_per_pixel 8, scanline_pad 32
depth 8, bits_per_pixel 8, scanline_pad 32
depth 15, bits_per_pixel 16, scanline_pad 32
depth 16, bits_per_pixel 16, scanline_pad 32
depth 24, bits_per_pixel 32, scanline_pad 32
depth 32, bits_per_pixel 32, scanline_pad 32
keycode range: minimum 8, maximum 255
focus: window 0x3c00004, revert to Parent
number of extensions: 27
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
default screen number: 0
number of screens: 1

screen #0:
dimensions: 800x600 pixels (344x191 millimeters)
resolution: 59x80 dots per inch
depths (7): 24, 1, 4, 8, 15, 16, 32
root window id: 0xfb
depth of root window: 24 planes
number of colormaps: minimum 1, maximum 1
default colormap: 0x20
default number of colormap cells: 256
preallocated pixels: black 0, white 16777215
options: backing-store NO, save-unders NO
largest cursor: 800x600
current input event mask: 0xfa8033
KeyPressMask KeyReleaseMask EnterWindowMask
LeaveWindowMask ExposureMask StructureNotifyMask
SubstructureNotifyMask SubstructureRedirectMask FocusChangeMask
PropertyChangeMask ColormapChangeMask
number of visuals: 64
default visual id: 0x21
visual:
visual id: 0x21
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xbc
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xbd
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xbe
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xbf
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc0
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc1
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc2
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc3
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc4
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc5
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc6
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc7
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc8
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xc9
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xca
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xcb
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xcc
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xcd
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xce
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xcf
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd0
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd1
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd2
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd3
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd4
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd5
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd6
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd7
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd8
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xd9
class: TrueColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xda
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xdb
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xdc
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xdd
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xde
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xdf
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe0
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe1
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe2
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe3
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe4
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe5
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe6
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe7
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe8
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xe9
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xea
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xeb
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xec
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xed
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xee
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xef
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf0
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf1
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf2
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf3
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf4
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf5
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf6
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf7
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf8
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0xf9
class: DirectColor
depth: 24 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
visual:
visual id: 0x3b
class: TrueColor
depth: 32 planes
available colormap entries: 256 per subfield
red, green, blue masks: 0xff0000, 0xff00, 0xff
significant bits in color specification: 8 bits
rayston@rayston-laptop:~$ ^C
rayston@rayston-laptop:~$ ^C
rayston@rayston-laptop:~$

---

### Post by sandeep.kapse85@gmail.com on 2010-02-07
[SIZE=4]**( This is not solution )**[/SIZE]


[SIZE=3]I am also having the same problem.[/SIZE]
[SIZE=3]
"[SIZE=2][B]I have a brand new Acer Aspire 5740-5513 and I installed Ubuntu 9.10 and the first thing I am having an issue with is that I cannot set the resolution above 800 x 600. I should be able to set it to 1388 x 768."


[/B][SIZE=3]I tried for other linux destro like suse , fedora and it works fine for the given resolution. I also tried for window (7) as well for macintosh ( hackintosh ) and it works fine for given resolution.

I did these things to cross check whether it is porblem with ubuntu or it's actual hardware limitation.

But the problem is only with ubuntu.

So if any one have idea about these things then please reply.
I use ubuntu for daily work and don't want to migrate to other destro as i am comfortable ubuntu.

Thanks.
[/SIZE][/SIZE][/SIZE]

---

### Post by stacktracer on 2010-02-07
You need two things: a new-ish xorg intel driver, and a new-ish kernel.

For the driver, use the xorg-edgers ppa ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)). Add it to your sources.list, then do an update and a dist-upgrade.

For the kernel, you need at least 2.6.32. (Works for me with 2.6.32.7.) Get kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). (It's not an apt repository, unfortunately -- you have to download the debs and install with dpkg.)

Those mainline kernel packages seem to be just straight vanilla kernels, with no Ubuntu-izations. The only practical difference I've seen so far is that AppArmor doesn't work, which is no big deal for me.

---

### Post by stacktracer on 2010-02-07
Forgot to add: in xorg.conf, replace "vesa" with "intel".

---

### Post by stacktracer on 2010-02-07
Also, even with xorg-edgers and kernel 2.6.32, compiz is unusably crashy.

You can turn it off with:

```
gconftool-2 --set /desktop/gnome/session/required_components/windowmanager --type string metacity
```

Of course, you first have to be able to log in ... which is tough with a crashy window manager, and bleeding-edge modesetting. I recommend booting with the "text" kernel parameter (press "e" at the grub boot menu), turn off compiz, then reboot as usual.

---

### Post by Rayston on 2010-02-07
Are there no better fixes for this problem? I am a bit of a newbie and upgrading my kernel sounds complicated. Would I be better off just installing 9.04?

---

### Post by Rayston on 2010-02-08
I went ahead and did this and now my resolution is fixed. 

Thank you so much.

---

### Post by Giggity on 2010-02-09
I'll add that stacktracer's advice worked for me as well.  Apparently the new driver and kernel support this setup.  Thanks a lot!

---

### Post by SonicSteve on 2010-03-04
I did a fresh install, initial troubles existed.
I had to install with safe graphics mode. This uses the VESA driver.

I then had to install all updates for ubuntu, reboot, then change the xorg.conf file from VESA, to INTEL.

Reboot and everything seems to be good.

I forgot to mention that I installed onto an ASUS K52F laptop. It must use the same arrandale chip.

---

### Post by krnewell on 2010-03-28
I have an Asus i3 laptop and was having the same issues. After digging around and switching to the edgers driver I was still getting a max res of 1024x768 and 16 bit color until I looked at this page:

[http://intellinuxgraphics.org/2](http://intellinuxgraphics.org/2) 009Q4.html

It states very clearly that kernel modesetting is the only method supported for detection of resolution. For some reason though this didn't seem to be working accurately when I was loading the intel driver (did work fine in vesa).

Following the tip for creating the file "/etc/modprobe.d/i915-kms.conf" with the line "options i915 modeset=1" seems to have worked. it manually forces KMS; even though it should already be forced this did allow detection of my panel and without this line it did not.

I'm still not getting much on acceleration, but atleast my resolution and color depth are normal again...

---


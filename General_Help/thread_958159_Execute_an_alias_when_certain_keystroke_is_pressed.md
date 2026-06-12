---
title: "Execute an alias when certain keystroke is pressed?"
date: 2008-10-25
forum: General Help
---

### Post by crazyfuturamanoob on 2008-10-25
Hello. My firefox crashes/freezes really often, so I have an alias for killing the firefox process and restarting it.
But I have to type it in console every time. I want to press a keystroke to execute the alias. How to do this?

---

### Post by tonybaqain on 2008-10-25
i believe sticking with the problem is a problem itself, try updating firefox ...

either **sudo apt-get remove firefox && sudo apt-get install firefox** or download it from [www.firefox.com](www.firefox.com) and click on download, you'll have a better life.

have fun :)

---

### Post by crazyfuturamanoob on 2008-10-25
Doesn't work. I have tried. Firefox just freezes on some youtube videos.

---

### Post by glotz on 2008-10-25
The problem is the buggy adobe flash plugin. Remove it and use gnash.

---

### Post by sethvath on 2008-10-25
A tutorial on alias, look under Aliasing Commands

[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)

To fix your firefox issue, which flash plugin are you using? 9 or 10, 32 bit or 64 bit?

---

### Post by crazyfuturamanoob on 2008-10-25
> **sethvath said:**
> A tutorial on alias, look under Aliasing Commands

[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)

To fix your firefox issue, which flash plugin are you using? 9 or 10, 32 bit or 64 bit?

I don't know about that flash plug in. Perhaps there is a console command to check it?

---

### Post by crazyfuturamanoob on 2008-10-25
> **glotz said:**
> The problem is the buggy adobe flash plugin. Remove it and use gnash.

Installed gnash and mozilla-plugin-gnash but now I can't see ANYTHING in youtube.

---

### Post by kerry_s on 2008-10-25
in firefox type:
```
about:plugins
```

to see what flash version you have.

some thoughts:

in /etc/firefox/firefoxrc

try adding:

XLIB_SKIP_ARGB_VISUALS=1
export XLIB_SKIP_ARGB_VISUALS=1


don't bother with the open source flash, make sure there all uninstalled, several kinds of flash, could be causing the problem.

---

### Post by sethvath on 2008-10-25
Firstly are you using 32bit or 64bit ubuntu?

To check the version of flash, type ```
about:plugins
``` in firefox and look for shockwave flash. 

There are 109187726726826287227862726272 other tutorials to getting flash 10 on firefox, here is just 1 of them

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

---

### Post by crazyfuturamanoob on 2008-10-25
32 bit ubuntu. I removed gnash plugins and then I edited my /etc/firefox/firefoxrc. I added the two lines, but the file was originally like this:
```
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.
```
It isn't similar than the one kerry_s posted. Should I add the all other lines too?

And I noticed now I get some serious laag with that flashplugin (adobe's one).
At least I can see something.

Edit: Tried sethvath's way too. Didn't work either. Horrible laag.

---

### Post by kerry_s on 2008-10-25
> **crazyfuturamanoob said:**
> 32 bit ubuntu. I removed gnash plugins and then I edited my /etc/firefox/firefoxrc. I added the two lines, but the file was originally like this:
```
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.
```
It isn't similar than the one kerry_s posted. Should I add the all other lines too?

And I noticed now I get some serious laag with that flashplugin (adobe's one).
At least I can see something.

Edit: Tried sethvath's way too. Didn't work either. Horrible laag.

no, i'm using iceweasel on debian etch, it looks different but does the same thing. the other 1 just disables pango for speed, i don't use other languages except english so i don't need that support.

whats your specs?
what vid card and are you using the right drivers?

ps: make sure you restart firefox after editing so the changes can take effect.

---

### Post by kerry_s on 2008-10-25
i was thinking, until you fix the problem. you could just create a desktop launcher or toolbar launcher with "killall firefox-bin" for the command.

for the keyboard shortcut you have to use the configuration editor(gconf-editor).

double click the "apps" folder
double click the "metacity" folder
click the global_keybindings folder
click run_command_1

then just put the command and keys you want to use.

---

### Post by crazyfuturamanoob on 2008-10-25
Ok. Now I uninstalled all other flash stuff and left only the flashplugin-nonfree.

It works without laag, but firefox crashes often. And with that keystroke, it is so fast to restart it (even all open web pages remain) that I don't need a better solution.

---

### Post by crazyfuturamanoob on 2008-10-25
I did that key trick but what is the keystroke? I tried ctrl+alt+f1 as gconf-editor said, but that killed gnome ](*,)

shitf+alt+f1 dont do anything.

---

### Post by kerry_s on 2008-10-25
> **crazyfuturamanoob said:**
> I did that key trick but what is the keystroke? I tried ctrl+alt+f1 as gconf-editor said, but that killed gnome ](*,)

shitf+alt+f1 dont do anything.

ohh, i'm not using gnome any more so i'm not exactly sure how it go's, but you got to use something that's not already in use, for example:

<Escape>f
might be
<ESC>f

try doing some googling, i'm sure others have done it.

can you post your /var/log/Xorg.0.log

maybe there's a clue in there.

you might also want to try starting firefox from terminal, that way you can see any errors.

---

### Post by crazyfuturamanoob on 2008-10-26
> **kerry_s said:**
> ohh, i'm not using gnome any more so i'm not exactly sure how it go's, but you got to use something that's not already in use, for example:

<Escape>f
might be
<ESC>f

try doing some googling, i'm sure others have done it.

can you post your /var/log/Xorg.0.log

maybe there's a clue in there.

you might also want to try starting firefox from terminal, that way you can see any errors.
Ok. I will edit my post when I have found that file, and my firefox either just closes, without warning or questions, or it freezes, without warnings or errors either. And when it does, only way to recover it is to kill it and restart.

Edit:
Here it is:
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux ohra-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 26 11:02:45 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0547 card 1025,0126 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0548 card 1025,0126 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0542 card 1025,0126 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,0541 card 10de,cb84 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,0543 card 1025,0126 rev a2 class 0b,40,00 hdr 80
(II) PCI: 00:02:0: chip 10de,055e card 1025,0126 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,055f card 1025,0126 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,055e card 1025,0126 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:04:1: chip 10de,055f card 1025,0126 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0560 card f025,0126 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,055c card 1025,0126 rev a1 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0561 card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:09:0: chip 10de,0550 card 1025,0126 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0a:0: chip 10de,054c card 1025,0126 rev a2 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,0562 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0563 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0563 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:04:0: chip 1180,0832 card 1025,0126 rev 05 class 0c,00,10 hdr 80
(II) PCI: 01:04:1: chip 1180,0822 card 1025,0126 rev 22 class 08,05,00 hdr 80
(II) PCI: 01:04:2: chip 1180,0592 card 1025,0126 rev 12 class 08,80,00 hdr 80
(II) PCI: 01:04:3: chip 1180,0852 card 1025,0126 rev 12 class 08,80,00 hdr 80
(II) PCI: 02:00:0: chip 10de,0425 card 1025,0126 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:00:0: chip 168c,001c card 1468,0428 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0500000 - 0xd05fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd1000000 - 0xd3ffffff (0x3000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[1] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[2] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[3] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd03fffff (0x200000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation GeForce 8600M GS rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd2000000/25, I/O @ 0x4000/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd0501000 - 0xd05010ff (0x100) MX[B]
	[1] -1	0	0xd0500c00 - 0xd0500cff (0x100) MX[B]
	[2] -1	0	0xd0500800 - 0xd05008ff (0x100) MX[B]
	[3] -1	0	0xd0500000 - 0xd05007ff (0x800) MX[B]
	[4] -1	0	0xd0889800 - 0xd088980f (0x10) MX[B]
	[5] -1	0	0xd0889c00 - 0xd0889cff (0x100) MX[B]
	[6] -1	0	0xd0888000 - 0xd0888fff (0x1000) MX[B]
	[7] -1	0	0xd0884000 - 0xd0885fff (0x2000) MX[B]
	[8] -1	0	0xd0880000 - 0xd0883fff (0x4000) MX[B]
	[9] -1	0	0xd0889400 - 0xd08894ff (0x100) MX[B]
	[10] -1	0	0xd0887000 - 0xd0887fff (0x1000) MX[B]
	[11] -1	0	0xd0889000 - 0xd08890ff (0x100) MX[B]
	[12] -1	0	0xd0886000 - 0xd0886fff (0x1000) MX[B]
	[13] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0600000 - 0xd067ffff (0x80000) MX[B]
	[17] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[18] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[19] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[20] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[21] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[22] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[23] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[24] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[25] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[26] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[27] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[28] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd0400000 - 0xd040ffff (0x10000) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0501000 - 0xd05010ff (0x100) MX[B]
	[1] -1	0	0xd0500c00 - 0xd0500cff (0x100) MX[B]
	[2] -1	0	0xd0500800 - 0xd05008ff (0x100) MX[B]
	[3] -1	0	0xd0500000 - 0xd05007ff (0x800) MX[B]
	[4] -1	0	0xd0889800 - 0xd088980f (0x10) MX[B]
	[5] -1	0	0xd0889c00 - 0xd0889cff (0x100) MX[B]
	[6] -1	0	0xd0888000 - 0xd0888fff (0x1000) MX[B]
	[7] -1	0	0xd0884000 - 0xd0885fff (0x2000) MX[B]
	[8] -1	0	0xd0880000 - 0xd0883fff (0x4000) MX[B]
	[9] -1	0	0xd0889400 - 0xd08894ff (0x100) MX[B]
	[10] -1	0	0xd0887000 - 0xd0887fff (0x1000) MX[B]
	[11] -1	0	0xd0889000 - 0xd08890ff (0x100) MX[B]
	[12] -1	0	0xd0886000 - 0xd0886fff (0x1000) MX[B]
	[13] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0600000 - 0xd067ffff (0x80000) MX[B]
	[17] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[18] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[19] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[20] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[21] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[22] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[23] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[24] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[25] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[26] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[27] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[28] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0400000 - 0xd040ffff (0x10000) MX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0501000 - 0xd05010ff (0x100) MX[B]
	[5] -1	0	0xd0500c00 - 0xd0500cff (0x100) MX[B]
	[6] -1	0	0xd0500800 - 0xd05008ff (0x100) MX[B]
	[7] -1	0	0xd0500000 - 0xd05007ff (0x800) MX[B]
	[8] -1	0	0xd0889800 - 0xd088980f (0x10) MX[B]
	[9] -1	0	0xd0889c00 - 0xd0889cff (0x100) MX[B]
	[10] -1	0	0xd0888000 - 0xd0888fff (0x1000) MX[B]
	[11] -1	0	0xd0884000 - 0xd0885fff (0x2000) MX[B]
	[12] -1	0	0xd0880000 - 0xd0883fff (0x4000) MX[B]
	[13] -1	0	0xd0889400 - 0xd08894ff (0x100) MX[B]
	[14] -1	0	0xd0887000 - 0xd0887fff (0x1000) MX[B]
	[15] -1	0	0xd0889000 - 0xd08890ff (0x100) MX[B]
	[16] -1	0	0xd0886000 - 0xd0886fff (0x1000) MX[B]
	[17] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0600000 - 0xd067ffff (0x80000) MX[B]
	[21] -1	0	0xd0400000 - 0xd040ffff (0x10000) MX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[25] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[26] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[27] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[28] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[29] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[30] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[31] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[32] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[33] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[34] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[35] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.12  Thu Jul 17 18:36:35 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  173.14.12  Thu Jul 17 18:15:54 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:1:3) found
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0501000 - 0xd05010ff (0x100) MX[B]
	[5] -1	0	0xd0500c00 - 0xd0500cff (0x100) MX[B]
	[6] -1	0	0xd0500800 - 0xd05008ff (0x100) MX[B]
	[7] -1	0	0xd0500000 - 0xd05007ff (0x800) MX[B]
	[8] -1	0	0xd0889800 - 0xd088980f (0x10) MX[B]
	[9] -1	0	0xd0889c00 - 0xd0889cff (0x100) MX[B]
	[10] -1	0	0xd0888000 - 0xd0888fff (0x1000) MX[B]
	[11] -1	0	0xd0884000 - 0xd0885fff (0x2000) MX[B]
	[12] -1	0	0xd0880000 - 0xd0883fff (0x4000) MX[B]
	[13] -1	0	0xd0889400 - 0xd08894ff (0x100) MX[B]
	[14] -1	0	0xd0887000 - 0xd0887fff (0x1000) MX[B]
	[15] -1	0	0xd0889000 - 0xd08890ff (0x100) MX[B]
	[16] -1	0	0xd0886000 - 0xd0886fff (0x1000) MX[B]
	[17] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0600000 - 0xd067ffff (0x80000) MX[B]
	[21] -1	0	0xd0400000 - 0xd040ffff (0x10000) MX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[25] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[26] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[27] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[28] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[29] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[30] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[31] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[32] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[33] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[34] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[35] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0501000 - 0xd05010ff (0x100) MX[B]
	[5] -1	0	0xd0500c00 - 0xd0500cff (0x100) MX[B]
	[6] -1	0	0xd0500800 - 0xd05008ff (0x100) MX[B]
	[7] -1	0	0xd0500000 - 0xd05007ff (0x800) MX[B]
	[8] -1	0	0xd0889800 - 0xd088980f (0x10) MX[B]
	[9] -1	0	0xd0889c00 - 0xd0889cff (0x100) MX[B]
	[10] -1	0	0xd0888000 - 0xd0888fff (0x1000) MX[B]
	[11] -1	0	0xd0884000 - 0xd0885fff (0x2000) MX[B]
	[12] -1	0	0xd0880000 - 0xd0883fff (0x4000) MX[B]
	[13] -1	0	0xd0889400 - 0xd08894ff (0x100) MX[B]
	[14] -1	0	0xd0887000 - 0xd0887fff (0x1000) MX[B]
	[15] -1	0	0xd0889000 - 0xd08890ff (0x100) MX[B]
	[16] -1	0	0xd0886000 - 0xd0886fff (0x1000) MX[B]
	[17] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0600000 - 0xd067ffff (0x80000) MX[B]
	[21] -1	0	0xd0400000 - 0xd040ffff (0x10000) MX[B]
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[28] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[29] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[30] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[31] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[32] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[33] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[34] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[35] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[36] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[37] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[38] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600M GS (G86) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.51.00.33
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600M GS at PCI:2:0:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0):     Acer X221W (DFP-1)
(--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): Acer X221W (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer X221W (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0501000 - 0xd05010ff (0x100) MX[B]
	[5] -1	0	0xd0500c00 - 0xd0500cff (0x100) MX[B]
	[6] -1	0	0xd0500800 - 0xd05008ff (0x100) MX[B]
	[7] -1	0	0xd0500000 - 0xd05007ff (0x800) MX[B]
	[8] -1	0	0xd0889800 - 0xd088980f (0x10) MX[B]
	[9] -1	0	0xd0889c00 - 0xd0889cff (0x100) MX[B]
	[10] -1	0	0xd0888000 - 0xd0888fff (0x1000) MX[B]
	[11] -1	0	0xd0884000 - 0xd0885fff (0x2000) MX[B]
	[12] -1	0	0xd0880000 - 0xd0883fff (0x4000) MX[B]
	[13] -1	0	0xd0889400 - 0xd08894ff (0x100) MX[B]
	[14] -1	0	0xd0887000 - 0xd0887fff (0x1000) MX[B]
	[15] -1	0	0xd0889000 - 0xd08890ff (0x100) MX[B]
	[16] -1	0	0xd0886000 - 0xd0886fff (0x1000) MX[B]
	[17] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0600000 - 0xd067ffff (0x80000) MX[B]
	[21] -1	0	0xd0400000 - 0xd040ffff (0x10000) MX[B]
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[28] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[29] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[30] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[31] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[32] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[33] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[34] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[35] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[36] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[37] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[38] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0):     file path under /proc/acpi/video NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

```

---


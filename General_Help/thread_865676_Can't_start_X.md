---
title: "Can't start X"
date: 2008-07-20
forum: General Help
---

### Post by dbbolton on 2008-07-20
I have tried Arch, Debian lenny, and lastly Ubuntu Server on my desktop. I absolutely cannot get X going (all though it seemed to work fine on Debian etch). I have an ATI All in Wonder 9600, so I have been using the 'ati' driver (that's the one that worked in etch).

When I try to start X, I get this happens:

```

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 20 19:43:16 2008
(==) Using config file: "/etc/X11/xorg.conf"

(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL
finished output detect: 0
finished output detect: 1
finished output detect: 2
(EE) RADEON(0): No connected devices found!
finished all detect
before xf86InitialConfiguration
(EE) RADEON(0): Using VGA default
in RADEONProbeOutputModes
(EE) RADEON(0): Output VGA-1 enabled but has no modes
(EE) RADEON(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```my xorg.conf
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "itouch"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "aiw9600"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "synaps"
        HorizSync       31.5
        VertRefresh     50-90
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "synaps"
        Device          "aiw9600"
        DefaultDepth    24
   Subsection           "Display"
                Depth           24
                Modes           "1024x768"
                Viewport        0 0
   EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```I have also tried the 'vesa' driver, which didn't work. Can anyone help me? I'm pulling my hair out.

---

### Post by meoblast001 on 2008-07-20
i heard ATI has terrible Linux support. I'd recommend a new GPU. :(

---

### Post by dbbolton on 2008-07-20
> **meoblast001 said:**
> i heard ATI has terrible Linux support. I'd recommend a new GPU. :(
I've had success with both ATI and nVidia in the past. As I said, X worked fine on Debian etch, so I know it's possible to use this card with linux.

---

### Post by ibuclaw on 2008-07-20
[**EDIT2**]
OK, I actually have the agility to make one up for you using pretty much the standard basics...
No guarantees that it'll work though.
[/**EDIT2**]


Hmm... that xorg file looks a bit wrong...
I am going to assume you know how to work things, so here is my xorg.conf file, make changes to it to match your system. (I would leave out the "Subsection Display" and the "BusID" options, they don't look right...
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"itouch"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

Regards
Iain

---

### Post by dbbolton on 2008-07-20
> **tinivole said:**
> [EDIT]
If you are reading this, it is OK to proceed :)
I've just removed the nvidia-specific lines from my xorg file.
[/EDIT]


Hmm... that xorg file looks a bit wrong...
I am going to assume you know how to work things, so here is my xorg.conf file, make changes to it to match your system. (I would leave out the "Subsection Display" and the "BusID" options, they don't look right...
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Regards
Iain
Every xorg.conf that I've had on a working X has had the Display subsection as well as the BusID, so that's why I added them. Anyhow, I mv'ed my xorg.conf and tried startx to force X to use the default settings, and that didn't work, so I know the problem isn't with the xorg.conf file. Thanks anyhow.

---

### Post by ibuclaw on 2008-07-20
Well, the output information kinda gives it away that it could be that your PCI card Bus location isn't configured properly on the Xorg.
> 
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) RADEON(0): No connected devices found!
(EE) RADEON(0): Using VGA default
(EE) RADEON(0): Output VGA-1 enabled but has no modes
(EE) RADEON(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.


Regards
Iain

---

### Post by dbbolton on 2008-07-20
> **tinivole said:**
> Well, the output information kinda gives it away that it could be that your PCI card Bus location isn't configured properly on the Xorg.


Regards
Iain
Output of lspci | grep VGA:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
```

That's why I set it to 
PCI:1:0:0

---

### Post by dbbolton on 2008-07-20
Just in case there was a problem with my xorg.conf, I ran dpkg-reconfigure xserver-xorg.

Here is my current xorg.conf:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "itouch"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

Here is the output of startx:
```

xauth:  error in locking authority file /home/daniel/.Xauthority
xauth:  error in locking authority file /home/daniel/.Xauthority
xauth:  error in locking authority file /home/daniel/.Xauthority
xauth:  error in locking authority file /home/daniel/.Xauthority


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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux reddevil 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 20 23:07:20 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL
finished output detect: 0
finished output detect: 1
finished output detect: 2
(EE) RADEON(0): No connected devices found!
finished all detect
before xf86InitialConfiguration
(EE) RADEON(0): Using VGA default
in RADEONProbeOutputModes
after xf86InitialConfiguration
(II) Module "ramdac" already built-in
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 80140000
best_freq: 80140909
best_feedback_div: 653
best_ref_div: 55
best_post_div: 4
restore memmap
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
disable montype: 1
(II) Module "i2c" already built-in
(EE) RADEON(0): Microcode: cannot load microcode
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86MonBrightnessDown: line 149 of inet
expected keysym, got XF86MonBrightnessUp: line 150 of inet
expected keysym, got XF86KbdLightOnOff: line 153 of inet
expected keysym, got XF86KbdBrightnessDown: line 154 of inet
expected keysym, got XF86KbdBrightnessUp: line 155 of inet
expected keysym, got XF86Info: line 914 of inet
enable montype: 1
SetClientVersion: 0 9
SetKbdSettings - type: -1078728260 rate: 30 delay: 500 snumlk: 12
xinit:  connection to X server lost.

waiting for X server to shut down disable montype: 1
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


xauth:  error in locking authority file /home/daniel/.Xauthority

```

When I ran startx, my monitor said "No input signal" then turned off.

---


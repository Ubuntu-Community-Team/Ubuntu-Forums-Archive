---
title: "WSOD ATi Radeons and Drivers"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by briandu on 2007-11-13
Hi all,

I am pulling my hair out with the ATi Drivers. I have the following
AMD64 but using i386 Ubuntu 7.10 totally up to date
ATi Xpress 200 PCI

I have loaded the drivers using .sh script from ATi and I get WSOD
I have used Envy and get WSOD
I don't use proprietary and get WSOD
I have changed speed from 75Hz thru to 60Hz

It is very irregular as to when it happens.

I found using:
 cat /var/log/Xorg.0.log

results in an error message of driver and kernel incompatibility.
Here is the output:
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb76b2000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb76b2000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots


What do I do now?

Help!

---

### Post by briandu on 2007-11-14
Bump :popcorn:

---

### Post by briandu on 2007-11-14
so I carried on.....on my quest.

I then removed all Envy installs and made sure my ristricted drivers tickbox is off  and now is seems a reliable machine - HOWEVER only at 1024x768 and not 1280x1024. The Radeon XPRESS driver and the LCD seem to get in a tizz.

I have reinstalled the Envy again manually and has to reboot. The on bootup the xterm reconfig dialogue popped up. I tried various combos but noting seems to work?!!! So at present I am stuck at 1024x768.

Any ideas? At least I am not getting WSOD

---

### Post by briandu on 2007-11-15
:confused:
so I gave up and invoked the sudo dpkg-reconfigure -phigh xserver-xorg in order to reset everything.

It now works at 1280x1024! BUT it is not using the restricted ATi drivers. I give up at the moment.:mad::mad:

Maybe I need to change the ATi XPRESS 200 card? :(

Anyone? [-(:cry:

---

### Post by dralokyn on 2007-11-17
i've got the ati radeon xpress 1150, and while the monitor works and at the correct resolution, my system doesn't take any advantage of the power of the graphics card, such as 3d rendering. ati has recently decided to support linux, however, and they do have a driver on their website for the xpress 200.
from this page: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
select your correct linux architecture, then integrated/motherboard, then then radeon xpress 200. it will tell you the system requirements and give you detailed install instructions. hopefully that will work for you.

---

### Post by briandu on 2007-11-20
dralokyn, thanks for the link - however I did download that file and installed it as root as part of my experimenting AND I still get WSOD.

It drives me nuts as I cannot figure out why, Perhaps the card and screen are not matched. I am running 1280x1024@60Hz and it can remain stable for a couple of hours and then fail hopelessly.

I hae ticked the restricted drivers and used Envy but to no avail. It has just failed now.

I am open to any suggestions

---


---
title: "Toshiba A70 + RADEON 9000/9100 IGP - fglrx doesn't quite work"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by bonzini on 2006-11-08
Hi folks;

I have a Toshiba A70 with ATI RADEON 9000/9100 IGP (RS300M 5835) video.  I have been through Breezy, Dapper, and am now in edgy, and I have never quite been able to get fglrx completely working.

The long and the short of it is, no matter whose guide to installing fglrx I read, when I come to the end of the procedure, here is what I see:

> clh@dabuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

clh@dabuntu:~$ 

This despite the fact that I am running the fglrx driver:

> clh@dabuntu:~$ grep fglrx /var/log/Xorg.0.log
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x81e1b20
... etc

A deeper examination of Xorg.0.log shows that there is a problem, but I'm baffled as to what to do to fix it.

Right off, we see the following:

> (==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000c80
(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"
(==) fglrx(0): UseFastTLS=0

Hmm.  "DRI is not supported on Radeon...".  Does that mean I'm stuck forever without the fglrx support?

Also, look at that cool OpenGL Client Driver name: > on_igp9x00_we_do_not_support_dri.so

A little later on:

> (II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports

Again, a little further on:

> (II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7f55000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.28.8
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.

Still a bit further:

> (II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled

Hmmmm. :-k 

But then something does go wrong:

> drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(EE) AIGLX error: dlopen of /usr/lib/dri/on_igp9x00_we_do_not_support_dri.so failed (/usr/lib/dri/on_igp9x00_we_do_not_support_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0

OK, so I can now see why we have Mesa happening.  And sure enough,

> clh@dabuntu:~$ ls /usr/lib/dri/
atiogl_a_dri.so  i915_dri.so    r128_dri.so    s3v_dri.so     trident_dri.so
ffb_dri.so       i965_dri.so    r200_dri.so    savage_dri.so  unichrome_dri.so
fglrx_dri.so     mach64_dri.so  r300_dri.so    sis_dri.so
i810_dri.so      mga_dri.so     radeon_dri.so  tdfx_dri.so
clh@dabuntu:~$ 

doesn't show any evidence of that wonderful on_igp9x00_we_do_not_support_dri.so module.

So.  Does anybody have any ideas on this?

I don't know if it even really matters if I use fglrx, honestly.  But when I installed the 6.10 release, I left the standard video install alone for a few days and had some problems with the screen and mouse freezing up, so I decided to try fglrx once more.

Thanks in advance for any light you can shed on this!

---

### Post by bonzini on 2006-11-09
(bump)

Sorry to pester you folks, any ideas on this one?

---

### Post by piege on 2006-11-12
have the same problem...

---

### Post by g-clef on 2006-11-13
Apparently, ATI intentionally disabled DRI for the fglrx driver on the 9100 IGPs.  Why they did this is not clear.  I'm wrestling with this myself right now.  

If you use the "radeon" driver for Xorg (rather than fglrx), it will report that it loads DRI successfully, but still reports mesa in glxinfo (and no DRI).  I'll let you know if I manage to get DRI working with the radeon" driver on a 9100.

---

### Post by bonzini on 2006-11-14
> Apparently, ATI intentionally disabled DRI for the fglrx driver on the 9100 IGPs. Why they did this is not clear. I'm wrestling with this myself right now.

If you use the "radeon" driver for Xorg (rather than fglrx), it will report that it loads DRI successfully, but still reports mesa in glxinfo (and no DRI). I'll let you know if I manage to get DRI working with the radeon" driver on a 9100.
That would be super, thanks!

Just a comment on the Radeon driver; a couple of days ago, I stumbled on a thread around here talking about it, followed a link to the driver web site, and read the text there.

Seems to me that what I read indicated it **should** use the Mesa drivers, but that you should also expect pretty decent performance > 1000 on the gears.

Anyway, good luck getting it working.  I can't experiment to the extent implied by the radeon web site, just too busy with work and family right now to have my machine down at the same time. :confused:

---

### Post by bonzini on 2006-11-14
... and, whoops I just looked up Radeon on the wiki and guess what I found:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Might simplify things a bit :-)

---

### Post by Dale61 on 2006-11-14
Have been having problems with the graphics in my Satellite A30, and following the link as posted by Bonzini, I found the instructions also work with 6.06.

The instructions are supposed to be for Edgy, but now, I have 3D rendering on my ATI Radeon 9100.

---

### Post by drwatson on 2006-11-22
Hi Dale,

Are you also able to use the additional VGA port on your laptop now?
If so, how does your xorg.conf look?

Trying to get dual screen working on my pc with 9100 igp with vga + dvi under Dapper.

Greetings from Germany!

---

### Post by Dale61 on 2006-11-22
G'day drwatson.

I've not actually tried the VGA port, so I don't have an answer.

What I do know is that I tried something (can't remember exactly what though), and my xserver crashed.  I had to refer back to tseliot's thread for when the dodgy update caused all sorts of problems for a lot of people just to get back up and running.

I just checked, and when I type fglrxinfo into a terminal, I get 'bash: fglrxinfo: command not found'.

However, by doing glxinfo | grep rendering, direct rendering comes up as Yes.  Don't ask me how because prior to xserver crashing, I didn't have 3D, but once I had recovered it, 3D now works.  :confused: :confused:

---


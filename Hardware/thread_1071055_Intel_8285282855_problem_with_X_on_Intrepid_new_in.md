---
title: "Intel 82852/82855 problem with X on Intrepid: new in last month"
date: 2009-02-15
forum: Hardware
---

### Post by billharris on 2009-02-15
I've got a Toshiba A10 that ran Hardy nicely, and the upgrade to Intrepid went well.

Then about January 6 or later, I couldn't start X on the internal display.  I can run the various consoles, and I can display X on another machine using clients on that Toshiba.  When I try to log in, I get a typical login screen, but I can't type into the username box.

Based on some information I found early on, I uninstalled Compiz (I never was running Compiz, but somewhere someone suggested purging it).  

Here are the first lines of lspci output:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

Xorg.0.log is about 526 lines long; while I'll be glad to share it or other log files, if they help, it looks mostly okay.  The following two sections came closest to looking as if there might be a problem.  At the very end, it said:
(EE) intel(0): tried to update DSPARB with both planes enabled!
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
AUDIT: Sun Feb 15 08:57:59 2009: 5309 X: client 4 rejected from local host ( uid=0 gid=0 pid=5579 )
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!

Earlier in the file, it said:

(WW) intel(0): Chosen PLL clock of 66.6 Mhz more than 2% away from desired 65.0 Mhz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(WW) intel(0):   Hardware claims pipe A is on while software believes it is off
(WW) intel(0):   Hardware claims plane A is on while software believes it is off
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): [drm] dma control initialized, using IRQ 10
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled

Still earlier, it said:

(II) intel(0): I830CheckAvailableMemory: 947196 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
        (Cannot allocate memory)
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
        (Cannot allocate memory)
(II) intel(0): Tiled allocation successful.

This weekend, I downloaded a 8.10 LiveCD to see if it would work, but I get a black login screen.

Does this sound familiar?  Any suggestions as to what to fix or what to look at to find the problem?  I suspect the video didn't fail, for the login screen does show the typical Ubuntu login screens.

---

### Post by dkuhlman on 2009-02-16
> **billharris said:**
> I've got a Toshiba A10 that ran Hardy nicely, and the upgrade to Intrepid went well.

Then about January 6 or later, I couldn't start X on the internal display.  I can run the various consoles, and I can display X on another machine using clients on that Toshiba.  When I try to log in, I get a typical login screen, but I can't type into the username box.

(snip)

> This weekend, I downloaded a 8.10 LiveCD to see if it would work, but I get a black login screen.

Does this sound familiar?  Any suggestions as to what to fix or what to look at to find the problem?  I suspect the video didn't fail, for the login screen does show the typical Ubuntu login screens.

I'm also having trouble on a Toshiba laptop, mine a  Satellite A215-S4697.

In my case I can boot a with kernel 2.6.24-21 but not with 2.6.27-11 or 2.6.27-9.  With kernel 2.6.27, I can log on to a text console, but cannot start X windows.

Here are the last lines from Xorg.0.log after trying to boot:

```
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x78000000 FBMappedSize: 0x08000000
(EE) fglrx(0): FB pci_device_map_range error!(EE) fglrx(0): Failed to map FB memory
(II) fglrx(0): === [atiddxScreenInit] === end

Fatal server error:
AddScreen/ScreenInit failed for driver 0

(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
```

Do you think we are talking about the same bug?

Is this really an Xorg problem?  If so, where should I report it?

(an hour later ...)

OK.  Your talk about fglrx gave me an idea.  It seems to have solved my problem.  Here's what I did:

1. I booted with kernel 2.6.24.

2. Under Gnome, I used menu System-->Preferences-->Appearance to disable enhanced video effects (Compiz.

3. I used System-->Administration-->Hardware Drivers to deactivate fglrx.

4. Shut down and booted with kernel 2.6.27.  Yes! Now, I can.

5. I used System-->Administration-->Hardware Drivers to re-activate fglrx, which I believe, forced down-load of new drivers.

6. Used menu System-->Preferences-->Appearance to re-enable enhanced video effects.

7. Shut down and booted with kernel 2.6.27, just to make sure that I still can.

I do not understand what is going on here, so I don't know whether this will help in your case, but maybe ...

Anyway, thanks for giving me the hint that help me solve my problem.

- Dave

---

### Post by billharris on 2009-02-16
Dave, I'm glad I could be of help.  I wish it were from my depth of understanding. :-)

Is there a real quick way to explain how to boot with an earlier kernel?  I could probably look it up, but your other instructions seem so clear that I figure you could make that understandable in very short order.

Thanks,

Bill

---

### Post by billharris on 2009-02-16
Okay, I tried rebooting and found 2.26.24-21-generic in the list of options.  I tried that, but the login screen came up with a black background in the username box, and it wouldn't accept any typing (or the delay is measured in minutes or 10s of minutes).

Here's an idea: do those menu selections have command names?  Better expressed, how do I figure them out?  If I can run them remotely over X, I can do all the stuff you did from another machine.  Maybe that will work.

---

### Post by billharris on 2009-02-16
In System > Preferences > Main Menu, I found the commands.  Running gnome-appearance-properties froze the computer with the display, not the X client (!).  I had purged Compiz, though, so I figured that may not have been necessary.

After rebooting (I tried everything but restarting X, the likely obvious answer -- it was late at night), I tried jockey-gtk.  That only brought up a software modem, so I left it alone.

IOW, I'm glad that process worked for you, but I don't think it works for me unless someone can tell me the secret to running the CLI equivalent of gnome-appearance-properties or to getting an earlier kernel to run.

I'm considering downgrading to Hardy, but that seems extreme (and not guaranteed of success).  In any case, I won't likely do anything major today.

---

### Post by Holleyman on 2009-09-02
Is there any updates to this thread, did anyone ever figure out a solution?
I updated to 8.04 on my A10 laptop and cannot boot without black screen unless I use the recovery option on boot.  I have tried the:
#sudo apt-get remove xorg-driver-fglrx
 but it tells me fglrx isn't installed
I then try the next recommended line of 
# sudo dpkg-reconfigure -phigh xserver-xorg
It warns me that I am trying to overwrite and then does nothing.


Any help for a noob?

---


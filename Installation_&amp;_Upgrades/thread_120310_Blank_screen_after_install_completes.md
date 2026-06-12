---
title: "Blank screen after install completes"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by hartz on 2006-01-21
Hi there gurus!

I am fairly new to linux (though not to unix).  I have a simple stock instalation of Ubuntu running fine on my laptop and when Windows yet again gave me grief, decided to install it on my desktop computer as well.  After some grief with ubuntu taking very long to start the partitioner and several false starts, I managed to get Ubuntu (5.10) installed and booted.

The display however was just blank (With just an underscore in the top-left corner of the screen on both displays).  I used ALT-F1 etc to switch terminals but this did not work right away, though I suspected that the login screen was interfering with the switching process, and after a few tries, including CTRL-ALT-BACKSPACE and repeatedly trying, I managed to get a text console to appear.  Initially this just disappeared right away - seemed as if the system just decided to switch back to the GUI login session, but after a few more minutes of trying, I got a terminal session to stick, and I can log on there, from where I can now run commands, check mountpoints, running processes, etc.

So I switched back to the GUI session and blind entered my login name and password, and heard the logon sound over the speakers (Quite impresssive, but bound to become irritating later on I suspect).

So I am fairly sure that I have a running and correctly installed Ubuntu, but the X-Windows server config seems to be broken.  Can anybody help to get the X-windows display working; My pertinent hardware is as follow:

Gigabyte GV-3D1 display card based on dual GeForce 6600GT GPUs.
Rest of the system is quite normal, except that I have five S-ATA hard drives.

I am seriously out of touch with how to configure X-windows (The X server's name changed some time ago I seem to recall).  I suspect I will need to just initialy set the X config to use a simpler display mode to get it to work.  Once I've got it working, I can look at trying to get it to use the full capability of my monitors and display card.

Thanx,

P.S. This display card can also output to TV... it could be that the X display is currently active on the TV output to which I don't have anything connected.

P.P.S> netstat does not show any listening port on port 22:  How do I start an ssh daemon?

---

### Post by hartz on 2006-01-21
I've had some success:  I've done much searching and reading in the past hour, and I now have made some progress.  What I have now is the following:

The screen still goes blank (after booting up) showing only the non-flashing cursor, but then after another second or two, the screen goes completely black.  So I tried to move the mouse and a graphical pointer came into the viewable area from the side, on both screens.

I still cannot see the logon dialog, but after I log on I can see at least part of the display with a normal desktop background, as well as Application, Places, System menu etc on top and the status bar at the bottom (What are these called under Linux?)

Both screens show the same thing.  This is using the vesa driver and a modified xorg.conf file.  It appears that part of the desktop is not shown because I can move the mouse pointer off the display area, and then when I move back to the right, it takes some time to re-emerge, depending on how far I moved it over the edge of the monitor / viewable area.

In the xorg.conf I now have two sections each for device, monitor and screen, each only with an A or B to identify which screen, or device it is, etc.  In the ServerLayout section I have "Screen A" leftof "Screen B" as a second Screen line.  making Screen B the item on the first screen line gives me a corrupted display.

I continue my investigation and hope someone here can come to my rescue!

  _Hartz

P.s. Maybe someone can help me with a short instruction on how to properly stop X completely, and then restarting it to get it to reread xorg.conf.  I've tried gdm from the command line, but it tells me it is already running (Even when X spewed errors and did not seem to be running.  Currently I need to reboot to test each change, and it is slow going as I believe in changing one thing at a time!  Thanx

---

### Post by hartz on 2006-01-21
After killing X I suddenly got things the other way round.  I now see the login dialog, and aparently, the primary screen because there are now icons on the desktop for, for example the mounted disk drives.

Secondly the system is now running on only one screen, the other monitor is black.

I still have a part of the screen as not visible.  The one monitor remains black, yet the desktop clearly extends to this screen.  The applications often open off screen, but with Alt-F7, followed by arrow keys, I can move them into the viewable area.

Lastly, it does not seem to make any visible difference whether I use the nv driver, or the vesa driver

I can feel I am close to a breakthrough on this :-)

---

### Post by dueY on 2006-01-21
edit: Oops, didn't see the two replies after the inital post for some reason, so this may or may not be relevent anymore:

[QUOTE=hartz2]
GeForce 6600GT 
...
I am seriously out of touch with how to configure X-windows 
...
I suspect I will need to just initialy set the X config to use a simpler display mode to get it to work.  Once I've got it working, I can look at trying to get it to use the full capability of my monitors and display card.
[/QUOTE]

Looks like you have a pretty good idea of what is going on.  Try to get back to the console CTRL+ALT+F1.  Then type ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure the X.  Sounds like you know what to do from there (use "vesa" as your driver, go to nvidia.com and get the latest proprietary drivers, etc) Good luck!

---

### Post by christhemonkey on 2006-01-21
to stop GUI
sudo /etc/init.d/gdm stop
(replace stop with restart to restart it!)

If you are running startx, i believe it creates a new xorg.conf in your home folder (or it did with me anyway!) which had incorrect settings.  So a quick vi of this makes it possible to use.
sudo vi ~/xorg.conf

---

### Post by hartz on 2006-01-22
Hi there all!  Thanx to the guys who helped so far!  I am starting to seriously believe that I have hardware problems.  Here is why:

a) I have found some posts on forums that I believe should allow me to get my configuration to work in a multi-monitor display of some kind or another, yet I still have had no success.  I get the one screen to work, but not the other.

For the record, here are the links:
[INDENT][https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
[http://wiki.linuxquestions.org/wiki/Installing_NVIDIA_drivers](http://wiki.linuxquestions.org/wiki/Installing_NVIDIA_drivers)
[http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86](http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86)
[http://wiki.linuxquestions.org/wiki/Multiple_Monitors_with_Nvidia](http://wiki.linuxquestions.org/wiki/Multiple_Monitors_with_Nvidia)
[http://www.linuxquestions.org/questions/showthread.php?t=394180](http://www.linuxquestions.org/questions/showthread.php?t=394180)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

Note: I am still looking for a link to the nVidia Linux driver README file.
[/INDENT]

b) I have followed the suggestion on several pages to configure xorg first for one display, and then for the other, separately, to test that each display works properly.  (I previously skipped this because multi-display modes are working properly under Windows).  I found that the one display (BusID 5:0:0) works fine, but the other (BusID 4:0:0) does not do anything.

c) And finally, I found this in the Xorg.0.log file; You will notice that the NV(0) display reports a checksum problem on the V_BIOS.  Also, the "Found Monitors" reported does not make sense (to me).
```

...

(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(WW) NV(0): Bad V_BIOS checksum
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6600 GT"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xE8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: ___  Model: a990  Serial#: 402351
(II) NV(0): Year: 2005  Week: 8
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) NV(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported VESA Video Modes:
...
...
...
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(1): Initializing int10
(II) Truncating PCI BIOS Length to 64512
(--) NV(1): Chipset: "GeForce 6600 GT"
(**) NV(1): Depth 24, (--) framebuffer bpp 32
(==) NV(1): RGB weight 888
(==) NV(1): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/X11R6/lib/modules/libvgahw.a
(==) NV(1): Using HW cursor
(--) NV(1): Linear framebuffer at 0xD0000000
(--) NV(1): MMIO registers at 0xD8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/X11R6/lib/modules/libi2c.a
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(1): I2C bus "DDC" initialized.
(II) NV(1): Probing for analog device on output A...
(--) NV(1):   ...can't find one
(II) NV(1): Probing for analog device on output B...
(--) NV(1):   ...found one
(II) NV(1): Probing for EDID on I2C bus A...
(II) NV(1): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(1): I2C device "DDC:ddc2" removed.
(II) NV(1):   ... none found
(II) NV(1): Probing for EDID on I2C bus B...
(II) NV(1): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(1): I2C device "DDC:ddc2" removed.
(II) NV(1):   ... none found
(--) NV(1): CRTC 1 appears to have a CRT attached
(II) NV(1): Using CRT on CRTC 1
(--) NV(1): VideoRAM: 131072 kBytes
(==) NV(1): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(1): MonitorA: Using hsync range of 30.00-94.00 kHz
(II) NV(1): MonitorA: Using vrefresh range of 50.00-75.00 Hz
(II) NV(1): Clock range:  12.00 to 400.00 MHz
...

```

Note that despite this, Windows still is able to use both monitors for an extended desktop.  Also, in text mode, both monitors show the same thing.

---


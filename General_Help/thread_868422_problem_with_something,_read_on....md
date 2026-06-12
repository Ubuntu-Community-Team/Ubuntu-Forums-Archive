---
title: "problem with something, read on..."
date: 2008-07-23
forum: General Help
---

### Post by thyre on 2008-07-23
I don't know if this is wubi's problem so to speak, don't know a lot about this, so i will just describe the situation to you all.

Alright, I downloaded the wubi installer. Did all that jazz, restarted the computer, did the installer, everything seems to be fine, then it restarts again, and the log in screen comes up.

I enter username, i press enter, I enter password, i press enter. the login form thingy dissapears and leaves the log in background for maybe 10 seconds, the the screen goes completely dark as if its off(its not) then it pops back up with the log in screen. I repeat, and the same thing happens. Basically its a never ending login.

Please help.
thyre

---

### Post by thyre on 2008-07-24
Does anybody know what this problem is?

---

### Post by Sef on 2008-07-24
Please don't bump your thread, unless 24 hours have gone by.  Otherwise you can get an infraction for premature bumping.  Also everyone here is a volunteer, so answers sometimes are quick and sometimes are slow.  Please have patience.

---

### Post by ago on 2008-07-24
> **thyre said:**
> I don't know if this is wubi's problem so to speak, don't know a lot about this, so i will just describe the situation to you all.

Alright, I downloaded the wubi installer. Did all that jazz, restarted the computer, did the installer, everything seems to be fine, then it restarts again, and the log in screen comes up.

I enter username, i press enter, I enter password, i press enter. the login form thingy dissapears and leaves the log in background for maybe 10 seconds, the the screen goes completely dark as if its off(its not) then it pops back up with the log in screen. I repeat, and the same thing happens. Basically its a never ending login.

Please help.
thyre

It might be a problem with your video driver, check the xorg logs in /var/log if you boot in rescue mode you should be able to change that.

---

### Post by thyre on 2008-07-24
Im a linux noob, as I have seen people say.

Can you tell me how to do that? Dumb it down a little more?

I know how to choose the start up mode, just not check the logs...

---

### Post by minhmeoke on 2008-07-25
Boot into rescue mode by pressing esc at the Ubuntu boot menu, then choosing the rescue option. Once Ubuntu has loaded, enter the following into the prompt:

```
cat /var/log/Xorg.0.log
```

The problem should be in the last few lines, google for the solution. If you cannot find any errors, then you can step through the entire log with 

```
cat /var/log/Xorg.0.log | less
```

press q to quit once you have found the problem. You can see other logs by listing the contents of the /var/log folder.

```
ls /var/log
```

to view other logs, just replace the filename in the previous 2 commands.

---

### Post by thyre on 2008-07-25
I have no clue in the world what is going on here. I don't know how to fix any files or what not. Update though, I am able to log on, I switched the session to GNOME. I logged on, and now I have no toolbar, So for now I am looking through the files I need and and copying them to the desktop so I can access them through there. So ya, I have no toolbar, on top or bottom, But wait!

I was googling this matter and came across the package, i believe, gnome-panel. so i opened the terminal,and i typed gnome-panel I pressed enter, and wallah! the tool bar(top and bottom) came up.so I was like, alright, cool, thats done... no it isn't. I close the terminal, and the toolbar goes away. I have to have the terminal running with that code to have a tool bar. The immediate quoted text is realated to the toolbar.

> 
root@thyre-desktop:/home/thyre# gnome-panel

(gnome-panel:2827): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
[WARN  2827] kit-hash.c:206:kit_hash_insert(): key != NULL
 Not built with -rdynamic so unable to print a backtrace



This below here is everything that I saw that had a WW-warning, beside it, don't know if thats a problem or not. But that code is below here, This came up when I did the line by line code you told me to do. Thanks for all your help again, and I'm sorry if this is all confusing and Im asking for your help and your pretty much blind to it maybe? anyway, all help is greatly appreciated, and I well, appreciate it! :) THANKS!
> drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 410 x 256
(WW) Configured Mouse: No Device specified, looking for one...

> (WW) RADEON(0): Cannot read colourmap from VGA.  Will restore with default
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1

> enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 17
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x7fff7800 is: 0x7fff7800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x81ff8000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7800 0x7fff7800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x81ff8000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.

---

### Post by minhmeoke on 2008-07-28
Gnome, the desktop/window manager, seems to be acting strangely; for me the panels just worked out of the box. Maybe the installation got corrupted, you could try reinstalling wubi, or if you want the panels to appear from command line, type in gnome-panel& . The ampersand will run a program in the background, so you can reuse the prompt.

The ww messages seem to be coming from your ATI video card, I can't tell which model it is, and I have no experience with ATI, so sorry I can't help here. As long as you can get a graphical desktop, it shouldn't be an issue. You could try looking around for updated/new drivers, maybe that will fix something.

---


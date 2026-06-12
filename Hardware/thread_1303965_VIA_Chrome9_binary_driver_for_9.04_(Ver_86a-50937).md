---
title: "VIA Chrome9 binary driver for 9.04 (Ver 86a-50937)"
date: 2009-10-28
forum: Hardware
---

### Post by --dtk on 2009-10-28
Hey guys,

I just tried out via's new binary driver for 9.04[1] on my HP Mini 2133, but can't get it to work:

 * installed driver via the delivered vinstall script
 * ran depmod -a
 * restarted X

X dies with the error

```

(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo

```

The /etc/X11/xorg.conf states

```

dtk@minibox:~$ cat /etc/X11/xorg.conf | grep -A 8 "Section \"Device\""
Section "Device"
	#BusID "PCI:01:00:0"
	Driver 	"via"
	VendorName  	"VIA Tech"
	BoardName   	"via"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"		"EXA"
	Option		"MigrationHeuristic" "greedy"
EndSection
dtk@minibox:~$ cat /etc/X11/xorg.conf | grep ModulePath
       ModulePath   "/usr/lib/xorg/modules"
dtk@minibox:~$ ls -l /usr/lib/xorg/modules/drivers | grep via
-rwxr-xr-x 1 root root 818731 2009-10-28 22:10 via_drv.so
-rwxr-xr-x 1 root root 818731 2009-10-28 21:06 via_drv.so.viabak
dtk@minibox:~$ uname -r
2.6.28-16-generic
dtk@minibox:~$ ls -Fl -R /lib/modules/2.6.28-16-generic/kernel/drivers/gpu/ | grep via
drwxr-xr-x 2 root root   4096 2009-10-22 21:41 via/
drwxr-xr-x 2 root root   4096 2009-10-28 22:10 via_chrome9/
/lib/modules/2.6.28-16-generic/kernel/drivers/gpu/drm/via:
-rw-r--r-- 1 root root 58276 2009-10-20 23:56 via.ko
/lib/modules/2.6.28-16-generic/kernel/drivers/gpu/drm/via_chrome9:
-rwxr-xr-x 1 root root 62984 2009-10-28 22:10 via_chrome9.ko*
-rwxr-xr-x 1 root root 62984 2009-10-28 21:06 via_chrome9.ko.viabak*
dtk@minibox:~$ su -
Password:
root@minibox:/home/dtk# modprobe via; echo $?
0
root@minibox:/home/dtk# modprobe via_chrome9; echo $?
0
root@minibox:/home/dtk# exit
dtk@minibox:~$

```

I've tried several alternative xorg.conf files as well as done modifications myself, but the problem always seems to be loading the module.

I've searched for the error message, but I seem to be the only person on this planet unable to load that darn module :/

Anybody any idea what I'm doin' wrong? Anybody gotten the new bin to work?

Thanks for your help, mates
dtk


_____
[1]http://linux.via.com.tw/support/downloadFiles.action

---

### Post by azzert on 2009-10-29
Got same problem . Anyone helps ?

---

### Post by --dtk on 2009-10-29
Hi azzert,

in the meantime I built the previous version driver (Ver 86a-50283) that is available as source and installed it according to this[0] howto. Installing the XServer driver of it creates
```

root@minibox:~# ls -l /usr/lib/xorg/modules/drivers/via_drv.la 
-rwxr-xr-x 1 root root 939 2009-10-29 21:11 /usr/lib/xorg/modules/drivers/via_drv.la
root@minibox:

```

Afterwards I reinstalled the binary driver and merged the two xorg.conf files via provides with the two drivers (the resulting xorg.conf is based on the version coming with the self compiled driver and includes the options the newer version introduces).

This works more or less for me. Got 3D harware acceleration running. Don't know how to check whether 2D rendering is done in hardware :/ Before I stopped working on it today, the screen was somewhat blurred and kinda misaligned. Might be I need some modes in my xorg.conf.

Maybe you wanna keep an eye on this thread:
[http://ubuntuforums.org/showthread.php?t=1079314&page=29](http://ubuntuforums.org/showthread.php?t=1079314&page=29)
I got the impression pureblood and tom09 have a much better understanding of what the problem with via's god*** driver is than I have.

hth
dtk

__________
[0]https://wiki.ubuntu.com/LaptopTestingTeam/HP2133/CompileSourceHowTo

---

### Post by --dtk on 2009-10-29
> **--dtk said:**
>  Before I stopped working on it today, the screen was somewhat blurred and kinda misaligned. Might be I need some modes in my xorg.conf.
Fixed that blurry thingy:

```

Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1280x768" 80.14  1280 1344 1480 1680  768 769 772 795 -HSync +Vsync
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
      SubSection "Display"
        Depth      24
        Modes      "1280x768"
      EndSubSection
EndSection

```

This does it quite well for me.

Actually might attach my whole xorg.conf. Nothing special, really only merging existing configs.

I'll have to admit, though, that I'm not quite sure whether it was worth the fight. Really wanted to do this since videos in adobe's flash player (youtube) didn't play too smoothly, and I'm not sure it's any better by now :/ On the other hand, glxgears shows some 200-300FPS now (vs 20FPS with openchrome) for whatever it's worth.
My glxinfo looks like
```

dtk@minibox:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_MESA_copy_sub_buffer, 
    GLX_SGI_make_current_read, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_SGIX_fbconfig
OpenGL vendor string: S3/VIA Graphics, Incorporated
OpenGL renderer string: S3/VIA Graphics Chrome9 HC IGP
OpenGL version string: 1.4 15.13.18.01
OpenGL extensions:
   [...]

```

Not sure whether SGI is great for GLX. OpenGL seems to work, though.

*Really, really done with proprietary drivers*
*again*
dtk

---

### Post by --dtk on 2009-10-29
> **--dtk said:**
> Got 3D harware acceleration running.
w00ps. Maybe my 3D acceleration is not done quite as much in hardware as I thought it was -.- *doe*

Additionally, activating xrandr support via
```

Option "RandR" "true"

```
isn't working either.

> **--dtk said:**
> 
I'll have to admit, though, that I'm not quite sure whether it was worth the fight. Really wanted to do this since videos in adobe's flash player (youtube) didn't play too smoothly, and I'm not sure it's any better by now :/ On the other hand, glxgears shows some 200-300FPS now (vs 20FPS with openchrome) for whatever it's worth.
My glxinfo looks like

Yeah. If like *all* the acceleration is done in software, it isn't too surprising I'm not getting *that* much of a performance boost -.-

*thinks about getting rid of the via driver*
dtk

---

### Post by --dtk on 2009-10-29
btw, despite starting up, my /var/log/Xorg.0.log still states
```

(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo
(--) VIA(0): Chipset: "P4M900"
(--) VIA(0): Chipset Rev.: 0
(==) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor

```

The devil knows what graphics driver I am currently using :( *meh*

*surrender*
dtk

---

### Post by azzert on 2009-10-29
> **--dtk said:**
> Hi azzert,
Maybe you wanna keep an eye on this thread:
[http://ubuntuforums.org/showthread.php?t=1079314&page=29](http://ubuntuforums.org/showthread.php?t=1079314&page=29)
I got the impression pureblood and tom09 have a much better understanding of what the problem with via's god*** driver is than I have.



Someone posted patched drivers for via chrome9,( somewhere in last pages) .  I tried them, it's seems to work correctly , but i could'nt force X11 to turn LCD panel. I stuck with black screen :)

---

### Post by --dtk on 2009-10-29
> **azzert said:**
> Someone posted patched drivers for via chrome9,( somewhere in last pages) .  I tried them, it's seems to work correctly , but i could'nt force X11 to turn LCD panel. I stuck with black screen :)
You're talking about tom09's DRM patch? That won't compile with my current kernel, I'm afraid :/
```

dtk@minibox:~$ uname -r
2.6.28-16-generic
dtk@minibox:~$ 

```

What do you need them for? I think they're only required with newer kernels. The october binary seems to work with the current kernel, I think it's rather a matter of getting the xorg.conf right than patching the driver's functionality. imho. 

Actually I got the driver running, somewhat, but I still only have software acceleration *meh*

Guess I will just ask in the other thread, maybe someone's got a clue.

dtk

---

### Post by azzert on 2009-10-29
In my experience with VIA drivers , i learn that they'r allways bugged or something is wrong with them . 

I mean this post [http://ubuntuforums.org/showpost.php?p=8151398&postcount=260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260")

But i must addmit , probably you have got right this is not drivers fault. 

In logs I got something like : 
> II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x864" (vertical timing out of range)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)


Dont have any idea what to do with that .

---

### Post by --dtk on 2009-10-29
> **--dtk said:**
> Actually might attach my whole xorg.conf.

Slimmed down my xorg.conf to get rid of most of the warnings in the logs.
Maybe it helps to isolate the actual problems.

dtk

---

### Post by --dtk on 2009-10-29
> **azzert said:**
> I mean this post [http://ubuntuforums.org/showpost.php?p=8151398&postcount=260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260")
Uuh, nice one. thx. Hadn't read that one yet. Sounded promising, especially when reading [http://ubuntuforums.org/showpost.php?p=8154457&postcount=264](http://ubuntuforums.org/showpost.php?p=8154457&postcount=264).
But check out [http://ubuntuforums.org/showpost.php?p=8173670&postcount=272](http://ubuntuforums.org/showpost.php?p=8173670&postcount=272)
> **Susp said:**
> By the way, an _update_ turned up.

The driver I've introduced a week ago or something is now available at the Via, inc. [website]("http://linux.via.com.tw")
Therefore the driver posted in [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") is not something special anymore, I guess it is reasonable to leave the manual there.

;)

> **azzert said:**
> In logs I got something like : 
   ...
Dont have any idea what to do with that .

Methinks that's just the X server checking default resolutions and detecting they don't fit (vertical timing out of range == resolution too high). That's why I added the custom mode to my xorg.conf[0].

Anyway, those messages are only informational (II), *should* be nothing to worry about.

dtk

_________
[http://ubuntuforums.org/showpost.php?p=8191348&postcount=4](http://ubuntuforums.org/showpost.php?p=8191348&postcount=4)

---

### Post by LodeRunner on 2009-12-22
> **azzert said:**
> Someone posted patched drivers for via chrome9,( somewhere in last pages) .  I tried them, it's seems to work correctly , but i could'nt force X11 to turn LCD panel. I stuck with black screen :)

As I've mentioned [elsewhere]("http://ubuntuforums.org/showthread.php?t=965542&page=7"), the blank screen issue is somehow tied to the Broadcom wireless driver. It used to be only the proprietary wifi driver that would kill X after reboot, but since 9.10 the free driver does it as well. I've confirmed that this is the culprit, although this was without any manually installed video drivers.

EDIT: Actually, "kill X" is misleading.  As I recall, I was able to log in, click around the screen, and hear the sounds of apps launching.

---


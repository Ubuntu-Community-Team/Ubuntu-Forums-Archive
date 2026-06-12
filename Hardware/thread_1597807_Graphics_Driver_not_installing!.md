---
title: "Graphics Driver not installing!"
date: 2010-10-15
forum: Hardware
---

### Post by theparticle010 on 2010-10-15
Okay, I susally dont have this problem, I search for the model of the graphics card and download the driver from the website ( eg: Nvidia, or ati's website ) but for some reason the Driver manager didn't give me any notice that I needed a drigver for my ati card on an hp desktop, well anyways I followed the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

and anyways I tried to start up compiz with Alt+F2 "compiz --replace" and this works on everything else and, well simply nothing here, so I went to start up a game, Went to go start up assault cube, 

```
Using home directory: /home/ria2/.assaultcube_v1.1
current locale: en_US.UTF-8
init: sdl
init: net
init: world
init: video: sdl
init: video: mode
stacktrace:
/home/ria2/Desktop/Mitchell_Stuff/1.1.0.3/bin_unix/linux_64_client(_ZN12signalbinder11stackdumperEi+0x29) [0x4fc699]
/lib/libc.so.6(+0x33af0) [0x7ffda3eb1af0]
/usr/lib/fglrx/libGL.so.1(XF86DRIQueryVersion+0xae) [0x7ffda555f38e]
/usr/lib/fglrx/libGL.so.1(XF86DRIQueryExtension+0x79) [0x7ffda555f529]
/usr/lib/fglrx/libGL.so.1(+0x5ae3c) [0x7ffda555ee3c]
/usr/lib/fglrx/libGL.so.1(+0x3a51f) [0x7ffda553e51f]
/usr/lib/fglrx/libGL.so.1(+0x368d1) [0x7ffda553a8d1]
/usr/lib/fglrx/libGL.so.1(glXChooseVisual+0x3e) [0x7ffda553aaae]
/usr/lib/libSDL-1.2.so.0(+0x39bed) [0x7ffda527cbed]
/usr/lib/libSDL-1.2.so.0(+0x3ee9a) [0x7ffda5281e9a]
/usr/lib/libSDL-1.2.so.0(+0x3efc7) [0x7ffda5281fc7]
/usr/lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1cf) [0x7ffda5272acf]
/home/ria2/Desktop/Mitchell_Stuff/1.1.0.3/bin_unix/linux_64_client(_Z11setupscreenRiS_S_+0x1ac) [0x47404c]
/home/ria2/Desktop/Mitchell_Stuff/1.1.0.3/bin_unix/linux_64_client(main+0x22b) [0x47853b]
/lib/libc.so.6(__libc_start_main+0xfd) [0x7ffda3e9cc4d]
/home/ria2/Desktop/Mitchell_Stuff/1.1.0.3/bin_unix/linux_64_client() [0x435a09]
AssaultCube error (11) ()
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14


```

and anyways, I thought this was odd, but sometimes it just wont run, and a restart later it will run on my main computer, so I simply restarted, and had the same error again, so I started up Quake 3, and got this error

```
----------------------
5706 files in pk3 files
execing default.cfg
execing q3config.cfg
com_zoneMegs will be changed upon restarting.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.250
...setting mode 4: 800 600
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14
ria2@ria-desktop:~/ioquake3$ 

```

Now obviously this isn't all of what happened on startup, because ioquake 3 likes to cache and check file sin the memory as it's starting up... so it's quite long and I didn't see that I'd really need to post it here.

Now the thing i'm curious about it the fact that the both end with 

```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14

```

any ideas what when wrong... oh and by the way, I am running 64 bit ubuntu 10.04

---

### Post by Speed9044 on 2011-03-17
Hey I was having an issue with my graphics card driver as when when I installed ubuntu 10.10 on my hp laptop. I had added the medibuntu file source under my other download sources. I just searched for nvidia in the search bar and it popped up with a few driver for nvidia wasn't sure which one to get so I just installed the top one see if it would work if it didnt I'd remove it then install the next one. Well there were only 4 nvidia driver files so it didnt take long to find one that worked with my graphics card. Maybe it might work for you and your graphics card. what version do u have?

---

### Post by theparticle010 on 2011-03-18
It was a crappy embedded gfx card, to this day I still do not know what was really inside of the cheap HP computer, as I bought it from a school for my grandma for about $150, I have since sold the computer, and built one for her instead. It's some sort of rare embedded ATI card for sure, it's Linux support really sucks. Oh, and BTW, Nice way to revive a dead thread :) 

If you're wondering though, I did eventually get it working, I had to install OpenSUSE though ;)

---


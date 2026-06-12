---
title: "Compiz on your NVIDIA 8xxx series card- what works for you?"
date: 2008-09-05
forum: General Help
---

### Post by FokkerCharlie on 2008-09-05
Hello!

I have a nice new laptop, featuring, amongst other things, a core 2 Duo processor running at 2.0GHz, and a NVIDIA 8600M GS GPU.  However, the performance of compiz seems to be very sluggish, no matter what settings I tweak.  It all works, just nothing is smooth.

A minor complaint, in reality, of course, but if you have a similar GPU and get decent performance from it on compiz, please let us know- I think that there are plenty of people in a similar position!

Cheerio
Charlie

---

### Post by washeddang on 2008-09-05
I had similar issues with the Quadro NVS 140 in my laptop. Installing the latest beta binary drivers (177.70) from NVIDIA solved it for me.

You can download the latest drive here:
X86 - [ftp://download.nvidia.com/XFree86/Linux-x86/177.70/NVIDIA-Linux-x86-177.70-pkg1.run]("ftp://download.nvidia.com/XFree86/Linux-x86/177.70/NVIDIA-Linux-x86-177.70-pkg1.run")
X86-64 - [ftp://download.nvidia.com/XFree86/Linux-x86_64/177.70/NVIDIA-Linux-x86_64-177.70-pkg2.run]("ftp://download.nvidia.com/XFree86/Linux-x86_64/177.70/NVIDIA-Linux-x86_64-177.70-pkg2.run")

Instructions on how to install the driver can be found in this thread:
[http://ubuntuforums.org/showthread.php?t=797270&highlight=NVIDIA]("http://ubuntuforums.org/showthread.php?t=797270&highlight=NVIDIA")

---

### Post by FokkerCharlie on 2008-09-09
OK, I can give that a try.

I'm currently on 173.14.12 drivers from Envy.  Did installing the beta version cause any other issues?  If it doesn't work out, is it possible to get Envy to restore the previous state?

Charlie

---

### Post by washeddang on 2008-09-09
I've been running the beta for a while now without any issues... I think the uninstall option in Envy can remove the binary driver. However, if it doesn't, you can remove it by adding --uninstall to the install command:

sudo sh NVIDIA-Linux-x86_64-177.70-pkg2.run --uninstall

---

### Post by FokkerCharlie on 2008-09-09
Well, I successfully installed the beta driver, but I can't see any improvement in compiz or FlightGear.

Would you (or anyone else with a 8600M GS card) be kind enough to post what settings you have working for OpenGL?  Currently, I have:

Sync to VBlank, Allow Flipping both enabled, and Image Settings on High Perfomance.

Under compiz, I have tried various options, to no avail!

Cheers
Charlie

---

### Post by Pablo Pablovski on 2008-09-09
FWIW, I have an 8800GTS PCI-E (640MB version) and compiz runs really well on it using the 173 driver from EnvyNG - everything is smooth, virtually all of the plugins work (except window previews, for some reason). 

It worked equally well with the 169 driver from the repos.

The rest of my spec:

AMD 3500+ @ 2.4GHz
2GB RAM
kubuntu Hardy / and home both on a 16GB partition of a 250GB HDD

Not sure how to check the OpenGL config - presumably, it's still @ the default settings.

---

### Post by FokkerCharlie on 2008-09-09
Hi Pablo

Thanks for your input.  If you want to look at your nVidia OpenGL settings:

sudo apt-get install nvidia-settings

Then System - Admin - nVidia, and have a rummage!

Be interested to see what you have under OpenGL.

Cheers
Charlie

---

### Post by luxorvan on 2008-09-09
I am not using the 8xxx series just 7300le but if it's all installed right you should be able to use add/remove in menu to get nvidia x server settings, it will give you full control over the card. It will also tell you how well it's operating. Here is my x-server information:
Operating System:       Linux-x86_64
NVIDIA Driver Version: 177.13

X Server Information-----------------------------------------------------------------------------

Display Name:  xxxxxx-xxxxx

Server Version Number:   11.0
Server Vendor string:    The X.Org Foundation
Server Vendor Version    1.4.0.90 (10400090)

NV-Control Version:      1.17

X Screens:               1

I did however start from a fresh install of ubuntu and searched libc in synaptic. I scrolled through all the packages adding some I wasn't really sure were required but every thing works great! I added the apt-rpm and fakechroot, libc-dev. You can't rely on libc6 and the installer will state if you have libc or not! The installation was easy using only a terminal and saving the nvidia run file to my desktop! However if nvidia x server settings won't work. Your driver isn't installed right! If you need further help or info on how I did my NVIDIA installation? Just ask I'll share!

---

### Post by Pablo Pablovski on 2008-09-09
> **FokkerCharlie said:**
> Hi Pablo

Thanks for your input.  If you want to look at your nVidia OpenGL settings:

sudo apt-get install nvidia-settings

Then System - Admin - nVidia, and have a rummage!

Be interested to see what you have under OpenGL.

Cheers
Charlie

D'oh, I forgot about the nVidia settings app...
OK, I have allow flipping set, sync to v-blank unset. The quality slider is about 35% along from the left.

Under GLX, Direct Rendering is YES..

Good luck!

---

### Post by SIXAXIS on 2008-09-09
No problems with my MBP.

Core2Duo T8800 2.4GHz
nVidia 8600M GT
2 GB RAM

---

### Post by Lord Udedenkz on 2008-09-18
Am I the only one that cannot download the 177.70 driver from Nvidia? Is there another download server?

I hear that they might work better. :\

8600M GT User Here.

---

### Post by sensimilla on 2008-09-19
If you are using the beta driver (177.67 or higher) you need to do a few things to see the improvements.

from [http://nvnews.net/vbulletin/showthread.php?t=118088]("http://nvnews.net/vbulletin/showthread.php?t=118088")
> The 177.67 NVIDIA BETA Linux graphics driver release addresses several known 2D performance issues. However, some of these performance improvements rely on new and/or experimental features of the NVIDIA X driver, some of which are not yet enabled by default. In order to achieve optimal performance with the 177.67 X driver, please read the discussion of newly added and pre-existing performance tuning options.

Quick-start steps for the impatient:

- add these options to your X.Org configuration file:
Option "PixmapCacheSize" "1000000"
Option "AllowSHMPixmaps" "0" 
- after starting X, run:
# nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

This improved things for my 8800GT, see the linked thread for full details.

---

### Post by timothius on 2008-09-19
> **sensimilla said:**
> If you are using the beta driver (177.67 or higher) you need to do a few things to see the improvements.

from [http://nvnews.net/vbulletin/showthread.php?t=118088]("http://nvnews.net/vbulletin/showthread.php?t=118088")


This improved things for my 8800GT, see the linked thread for full details.


Hi, could you post your Xorg.conf file please?  I want to check where you put the options.

---

### Post by washeddang on 2008-09-19
You can put them in either the Screen or Device section. Here's my Device and Screen section:

```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
EndSection

Section "Screen"
    Identifier   "Screen0"
    Device       "Videocard0"
    Monitor      "Monitor0"
    DefaultDepth  24
    Option       "NoLogo" "True"
    Option       "OnDemandVBlankInterrupts" "True"
    Option       "PixmapCacheSize" "1000000"
    Option       "AllowSHMPixmaps" "0"
    Option       "TripleBuffer" "True"
    Option       "DamageEvents" "True"
    Option       "BackingStore" "True"
    Option       "RenderAccel" "True"
    Option       "AllowIndirectPixmaps" "True"
    Option       "AddARGBGLXVisuals" "True"
EndSection

```

---

### Post by FokkerCharlie on 2008-09-20
OK, I am still getting hiccups.  I found this on the Nvidia site:
[http://www.nvnews.net/vbulletin/showthread.php?t=77030]("http://www.nvnews.net/vbulletin/showthread.php?t=77030")
Which suggests entering this in a terminal:
```

ldd `which compiz`
```

And I get the response:
```

not a dynamic executable
```

Where I should see a link to libnvidia-tls.so.1 .  So it looks like compiz is not linked to Nvidia, which is strange.  Can anyone else try this on their machine?  Or perhaps give me any other clues?

Cheers
Charlie

---

### Post by liquidfunk on 2008-09-20
I'm using the 8500GT 512Mb Card, latest drivers, working like a dream for me.

---

### Post by sensimilla on 2008-09-20
> **FokkerCharlie said:**
> OK, I am still getting hiccups.  I found this on the Nvidia site:
[http://www.nvnews.net/vbulletin/showthread.php?t=77030]("http://www.nvnews.net/vbulletin/showthread.php?t=77030")
Which suggests entering this in a terminal:
```

ldd `which compiz`
```

And I get the response:
```

not a dynamic executable
```

I think that in Ubuntu the file called compiz is just a script that starts up compiz, I think the actual executable is called compiz.real. 

Sorry I can't test this as my compiz is currently uninstalled.

You may want to look into the power saving on the card, I'm pretty sure I have read that this can cause hiccups on laptops with compiz.

---

### Post by FokkerCharlie on 2008-09-20
OK, it's looking better my end since I added this to xorg.conf:

```
	Vendorname	"NVIDIA Corporation"
	#additional settings
	Option		"NoLogo"	"true"
	Option		"RandRRotation"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"OnDemandVBlankInterrupts"	"true"
	Option		"NvAGP"	"0"
	Option		"DamageEvents"	"true"
	Option		"UseEvents"	"true"
	Option		"PixmapCacheSize"	"200000"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"TripleBuffer"	"True"# Experimental
	Option		"BackingStore"	"True"# Experimental

```

Maybe this will help someone.  I do still see a few stutters, but I think that most of them are associated with Power Miser.

Cheerio
Charlie

---

### Post by borlosky on 2008-10-11
I'm using 8600gt 512 meg pci-e, 2 gigs ram, and core 2 duo 2.0, and all compiz effects work fine with restricted driver (new driver). the only effect i have any sort of issue with is the bicubic filter. that is to say, if the filter is enabled, the water effect no longer works, but water will work fine if i leave the filter turned off. other than that, no lag of any kind, even when running multiple effects at the same time. also as a side note, i guess i did also install compiz from git, and am not using the version thats in the repositories, and therefore plugins may not be 100% stable, so i guess that could explain my issue with the bicubic filter.

::edit:: i also run a second pc (older) ubuntu 8.04, p4 1.8ghz, 768m ram, geforce 6200 128meg agp. and all compiz effects run surprisingly smooth (if i don't have 20 programs all running at the same time that is, lol), i can have pidgin, firefox with 5+ tabs, bittornado and vlc all open/playing music, and cube, water, fire effects work pretty well/smooth. i do get a little lag once i start opening more from there... as to be expected with such an old system. also referring to the filter issue from before, this old pc uses compiz from repositories, i did not install from git, and bicubic filter works fine with water effect, but having the filter enabled, drastically slows the pc down.

---

### Post by loomsen on 2008-10-11
> **borlosky said:**
> I'm using 8600gt 512 meg pci-e, 2 gigs ram, and core 2 duo 2.0, and all compiz effects work fine with restricted driver (new driver). the only effect i have any sort of issue with is the bicubic filter. that is to say, if the filter is enabled, the water effect no longer works, but water will work fine if i leave the filter turned off. other than that, no lag of any kind, even when running multiple effects at the same time.

#2

Basically everything works, separate X screens(laptop, LCD-TV), compiz on both, screensaver plugin on both independently, everything basically)

---


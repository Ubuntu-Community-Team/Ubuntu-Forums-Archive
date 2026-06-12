---
title: "[SOLVED] How to exit  X?"
date: 2008-11-26
forum: General Help
---

### Post by rsnow on 2008-11-26
I am trying to install Nvidia drivers. When I do the instructions from Nvidia, i.e., type sh NVIDIA-Linux-x86-177.82-pkg1.run

I get error: You appear to be running an X server; Please exit X before installing.

I guess I'm just denser than usual today. How does one exit X if that is part of the operating system?

---

### Post by sr20ve on 2008-11-26
ctrl-alt-f2 to switch to virtual terminal. ctrl-alt-f7 to switch back.

or

Edit your boot line from your grub menu.

Reboot, press esc on bootup to enter the grub menu. Select you default kernel, press e to edit. Put a space, then 1 at the end of the line. Press esc, then b to boot.

That will boot into runlevel one, and it is just a temporary edit, so it will not affect the next boot.

---

### Post by RATM_Owns on 2008-11-26
Like sr20vc said, only in a virtual terminal you have to type:
```
sudo /etc/init.d/gdm stop
```

---

### Post by Chunky Dunk on 2008-11-26
Press ctrl-alt-F1 (or F2-F6) to switch to a virtual console, then login. Once you've done that issue: ```
sudo /etc/init.d/gdm stop
``` to stop X, and to start it again issue: ```
sudo /etc/init.d/gdm start
```

But, is there a reason you don't want to use the nvidia drivers already in the repositories?

---

### Post by rsnow on 2008-11-26
First of all, thanks to all for the prompt responses and clear instructions.

Second, I didn't know there were Nvidia drivers available through ubuntu. I guess I should have checked. I just went to the Nvidia web site and downloaded the drivers they recommended and started trying to install them.

---

### Post by rsnow on 2008-11-26
Follow up question - where how to find the nvidia drivers in the repository? I did searh in synaptic with no results.

---

### Post by Chunky Dunk on 2008-11-26
Go to System >> Administration >> Hardware Drivers and it will search for the nvidia driver, and tell you how to enable it.

---

### Post by nzadLithium on 2008-11-26
First off try this way, click system, administration, Hardware drivers
This app should hopefully detect your card and give you some available drivers for it along with a recommendation of what you should use, you can use that app to install it.

If that doesn't work:

they are in synaptic, search nvidia

or you could try this, I'm not sure if it will install all the necessary components of the driver but on command-line 
sudo apt-get update
sudo apt-get install nvidia-glx-177

If it still doesn't work, can you post up your nvidia cards model number so we can find out what version of the driver will work for you? (I think ubuntu has 3 different versions of the nvidia drivers XD).

Oh chunky dunk already posted the first bit XD

---

### Post by Kareeser on 2008-11-26
Furthermore, give EnvyNG a try. Works with both nVidia or ATI graphics cards.

Still got its kinks, but it works well enough without having to compile your own drivers...

---

### Post by JPBodner on 2008-11-26
I'd like to play along. I don't think I have the right setup for my NVIDIA 9600 GT.   The system>admin>hardware drivers gives me these choices:

NVIDIA accelerated graphics driver (version 173)
"                                                  " (version 177) [Recommended]

I've been using the second one.  There is also a System>Administration>NVIDIA X server settings   choice in my menu system.   That seems to be appropriately setup, but my machine is slow to switch between windows and slow to scroll inside a window, so I don't think all is well.  Any help is much appreciated.

---

### Post by nzadLithium on 2008-11-26
cat /etc/X11/xorg.conf

post output here

---

### Post by JPBodner on 2008-11-26
Here is my xorg.conf.  Thanks in advance for your help! 


```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by rsnow on 2008-11-27
I don't want to interfere with JP's situation but mine is solved. It turned out that I needed to repair a broken pkg. Thanks to all for their help.

---

### Post by nzadLithium on 2008-11-27
I may be confusing myself with the ati drivers, but for some reason i'm remembering that you need to disable composite for glx to work properly?

try changing
	Option		"Composite"	"Enable"
to
	Option		"Composite"	"Disable"

see if you get a bit more performance like that :D

The other thing you can try is running glxgears (type glxgears in terminal) just to check that your 3d accelleration is actually enabled :D

My xorg.conf (i'm also running a nvidia card) has alot more modules loaded than yours does so if it's still running slow after you've checked those, we can give the extra modules a try :D

---

### Post by CatKiller on 2008-11-27
> **nzadLithium said:**
> I may be confusing myself with the ati drivers, but for some reason i'm remembering that you need to disable composite for glx to work properly?

I believe it used to be the case that they didn't used to work well together, but there is a "AllowGLXWithComposite" option that turns them both on.

Actually, this is what NVidia's Readme has to say on the subject > Option "AllowGLXWithComposite" "boolean"

    Enables GLX even when the Composite X extension is loaded. ENABLE AT YOUR
    OWN RISK. OpenGL applications will not display correctly in many
    circumstances with this setting enabled.

    This option is intended for use on X.Org X servers older than X11R6.9.0.
    On X11R6.9.0 or newer X servers, [B]the NVIDIA OpenGL implementation
    interacts properly by default with the Composite X extension[/B] and this
    option should not be needed. However, on X11R6.9.0 or newer X servers,
    support for GLX with Composite can be disabled by setting this option to
    False.

    Default: false (GLX is disabled when Composite is enabled on X servers
    older than X11R6.9.0).

(emphasis mine)

So if you're running a newer version of Ubuntu, it's not an issue any more. Anything after Breezy Badger (5.10) has a version of X newer than 6.9.

---

### Post by nzadLithium on 2008-11-28
kk so scratch that bit XD

Just try the glxgears and see if you have 3d accell :D

---

### Post by JPBodner on 2008-11-29
Yep.  I see the gears.   The thing I notice is that when I switch between windows by clicking on the tabs, the switch seems to be slower than I remember on earlier versions/my old machine.  (I upgraded to 8.10 and have a new box).   It's definitely slower than on windows (I dual boot)

---

### Post by nzadLithium on 2008-11-29
Mine seems to work fairly quickly, and i have alot more modules loaded than you, so maybe if we load them up it might go faster? :D

change:
```
Section "Module"
    Load           "glx"
EndSection
```
To:
```
Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
```

---


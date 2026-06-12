---
title: "Coolbits option not available"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by MrTripi on 2008-01-03
Hi, I currently have NVIDIA Driver Version 169.07 for my NVidia Geforce FX GO5200.  I'm trying to enable coolbits so I can overclock the core and memory bandwith by about 15% however I'm currently unable to locate it anywhre in the Nvidia X Server Settings.  

I tried installing the NClock_qt and Nclock_gk, however everytime I overclock the settings then restart my computer-they immediately revert back to normal.  Also-even after overcocking my settings, I can start up the Nvidia-Settings which will report that they're still at their default settings, so I'm not sure if it's working to begin with.  Any ideas?

---

### Post by Paul Moir on 2008-01-03
Just do it manually.  Open up a terminal and type this command:

sudo gedit /etc/X11/xorg.conf

Then find the section "Device" with something about NVIDIA in it, and after the BusID line add your own reading:
Option "Coolbits" "1"

Such as this:
```
Section "Device"
        Identifier      "NV34"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
 Option "Coolbits" "1"
        Option "AllowGLXWithComposite" "true"
EndSection

```

Write the file, log out, hit ctrl-alt-backspace to make sure the X server restarts, login and you're set.

By the way, that option won't do a think if driver isn't set to "nvidia".  If it's set to "nv", you'll have to load the restricted driver.

Before you get serious about messing around with your video stuff, it's best to back up your /etc/X11/xorg.conf file so you can replace it if things go bad.

---

### Post by MrTripi on 2008-01-04
here's what I did

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"Coolbits" "1"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

didn't do anything though :/

---

### Post by LeAstrale on 2008-01-04
> **MrTripi said:**
> here's what I did

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"Coolbits" "1"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

didn't do anything though :/

just a side question. does the  "NoLogo" "True" option remove the Nvidia logo that flashes just before GDM is ready to sign you in?

---

### Post by MrTripi on 2008-01-04
damn, i'm not sure what to do here.  The coolbits option just isn't there.  This is what I did in order, maybe I have the wrong nvidia drivers?

1) Installed Ubuntu, came with default (restricted?) drivers
2) Installed Envy, uninstalled Nvidia drivers then installed the latest 1.69 drivers
3) Solved a number of problems, however games like Nexuiz where running at 5frames a second which is clearly way too low even for my laptop
4) checked off the restricted drivers again in the restricted driver manager


Overview:
The restricted drivers are actually running great, however I've noticed that machine will slow down SIGNIFICANTLY for a few seconds at a time before spasming back to a normal frame rate.  It does this in just about any game, including Savage.  Even diablo 2 where my frames will range between 60 and 200fps.  they'll suddenly drop to 3fps.  

Not to get off topic, but is it possible that there's a conflicting program running in the background?  I'm not too savvy with Linux just yet, been a long time Windows drone.

---

### Post by MrTripi on 2008-01-04
> **astral-1 said:**
> just a side question. does the  "NoLogo" "True" option remove the Nvidia logo that flashes just before GDM is ready to sign you in?

Yes, it does remove the logo.  Is it possible the 1.69 drivers just aren't any good on Linux?  Is there a way to use Envy so I can install a different version, maybe there's a website like guru3d.com which supplies a list of drivers but for linux.

just a shot in the dark anyway :P

---

### Post by s0ury on 2008-01-04
I put it under screen0 and it worked.
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900_60 +0+0; 1280x800@60 +0+0; 1280x720@60$
        Option          "AddARGBGLXVisuals"     "True"
       [B] Option "Coolbits" "1"
[/B]EndSection

```
BTW, i change the clocks, and it doesn't move an inch, it says saved 2D clocks to 169MHz 100MHz (that's the deafault for 8600M GS) whatever i choose.
EDIT: it doesn't OVERclock, it can only UNDERclock, (at least for 2D i won't risk this stupid embedded cheapish card by overclocking the 3D (real) clocks)

---

### Post by MrTripi on 2008-01-04
> **s0ury said:**
> I put it under screen0 and it worked.
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900_60 +0+0; 1280x800@60 +0+0; 1280x720@60$
        Option          "AddARGBGLXVisuals"     "True"
       [B] Option "Coolbits" "1"
[/B]EndSection

```
BTW, i change the clocks, and it doesn't move an inch, it says saved 2D clocks to 169MHz 100MHz (that's the deafault for 8600M GS) whatever i choose.
EDIT: it doesn't OVERclock, it can only UNDERclock, (at least for 2D i won't risk this stupid embedded cheapish card by overclocking the 3D (real) clocks)

*bashes head on keyboard* I give up man, i just tried moving the coolbits comment all over the places.

---

### Post by LeAstrale on 2008-01-07
MRtrippi --> i would try switching to the vesa driver and then install the Nvidia driver 169.07 from fresh again and let it CONFIGURE you xorg.conf at the end of your Nvidia install

---

### Post by ph1 on 2008-01-26
I, too, cannot get coolbits to apply any settings that I put in.  It just reverts to its original settings.

Anyone know anything that might work?

Thanks.

---

### Post by LeAstrale on 2008-01-28
have any of you tried it with the new 169.09 driver?

---

### Post by ph1 on 2008-02-03
I have not, but I'll give it a shot and report back.

EDIT:  this driver seems to have fixed the problem in general.  The screen no longer flashes with changes in clock speeds (I removed the PerfLevelSrc line to see what would happen).  Hooray!

---

### Post by tomplast on 2008-07-07
> **s0ury said:**
> I put it under screen0 and it worked.
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900_60 +0+0; 1280x800@60 +0+0; 1280x720@60$
        Option          "AddARGBGLXVisuals"     "True"
       [B] Option "Coolbits" "1"
[/B]EndSection

```
BTW, i change the clocks, and it doesn't move an inch, it says saved 2D clocks to 169MHz 100MHz (that's the deafault for 8600M GS) whatever i choose.
EDIT: it doesn't OVERclock, it can only UNDERclock, (at least for 2D i won't risk this stupid embedded cheapish card by overclocking the 3D (real) clocks)

It's exactly like this for me too. I have a Dell XPS M1530 with a 8600 GT GPU and I can only underclock :/. It's a little annoying...

---

### Post by sdennie on 2008-07-07
Coolbits only allows you to underclock on laptop cards.  This has been stated by nvidia developers on their forums.

---

### Post by tomplast on 2008-07-07
> **vor said:**
> Coolbits only allows you to underclock on laptop cards.  This has been stated by nvidia developers on their forums.

Is it possible to bypass? Or should I stay away from it? As long as I keep track of the temperatures it should be fairly safe, right?

---


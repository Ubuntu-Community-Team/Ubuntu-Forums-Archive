---
title: "Radeon RV250 (Mobility FireGL 9000) drivers on 8.10"
date: 2009-03-13
forum: Hardware
---

### Post by FawkesRSP on 2009-03-13
I am running 8.10 on my laptop. The laptop has a over a gig of ram, a pentium-m 1.6 ghz and a radeon mobility RV250 video card. I've known for a while that linux isn't using a proprietary video accelerator but compiz fusion worked and i don't game on this thing so i wasn't too worried. now however i am trying to do streaming video (not just hd, youtube and such as well) and it all works but looks very choppy. while the computer isn't the greatest it worked under xp so i'm thinking its because the video drivers. when i do sudo lshw it shows the video card as: 

*-display UNCLAIMED
description: VGA compatible controller
product: Radeon RV250 [Mobility FireGL 9000]
vendor: ATI Technologies INC
physical id: 0
bus info: pci@0000:01:00.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: agp agp-2.0 pm bus_master cap_list
configuration: latency=66 mingnt=8

I've tried to follow the BinaryDriverHowToATI but I can't see a driver for this card on ATi's website and ubuntu will not let me turn on proprietary drivers for it as it doesn't register anything to install a driver for on the screen. Any suggestions?

Thanks

---

### Post by FawkesRSP on 2009-03-19
bump

---

### Post by hiksebehessde on 2009-03-28
same issue here! can't find the catalyst driver on the ati website!!




xbsd@xbsd-kubuntu:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)


(bump)

---

### Post by orawax on 2009-04-22
I'm on Jaunty already, but this might work also with Intrepid. If it doesn't, then I suggest upgrading to Jaunty.

First I updated xorg.conf by issuing

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

In Jaunty, this default configuration enabled direct rendering for me without any extra tweaks and also corrected the graphical corruption I was experiencing after the upgrade. However, the GPU was still heating a LOT and graphics was really slow. Looking into some threads, I decided to modify the new xorg.conf by adding

Under Section "Screen" (here you should define the maximum real resolution of your display):
```
	Subsection "Display"
		Depth	24
		Modes	"1440x1050"
		Virtual 1440 1050
	EndSubSection
```

and under Section "Device"
```
	Option	"AccelMethod" "XAA"
	Option	"XAANoOffscreenPixmaps" "true"
```

So that my xorg.conf now looks like this:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Subsection "Display"
		Depth	24
		Modes	"1440x1050"
		Virtual 1440 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option	"AccelMethod" "XAA"
	Option	"XAANoOffscreenPixmaps" "true"
EndSection
```

Now compiz works fine, although I've disabled many of the effects (animations and wobbly windows for instance), since the 32mb of GPU memory just isn't enough to handle everything smoothly I guess. But I have what I most like in compiz, for instance transparency and shadows.

---

### Post by Safwan Khan on 2009-05-16
Thank you orawax! It works like a charm!! :D
Thanks for sharing!

---

### Post by orawax on 2009-09-30
Forget the above, this seems to work perfectly, at least in 9.10:
[http://ubuntuforums.org/showpost.php...12&postcount=2](http://ubuntuforums.org/showpost.php...12&postcount=2)

(See also postcount=3...)

---

### Post by ChuckMcB on 2009-12-02
orawax, can you repost the link as the forum garbled it. Thanks.

---

### Post by orawax on 2009-12-03
[http://ubuntuforums.org/showpost.php?p=7804812&postcount=2](http://ubuntuforums.org/showpost.php?p=7804812&postcount=2)

The original comments are in Finnish, so here's the same with rough English translation

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	# Useful for all ATI/AMD-cards
	Option	"AccelMethod"	"EXA" # Without this the ati-driver uses the older XAA -method
	Option	"DynamicClocks"	"true"	# An energy saving option
	# The following are useful only on Mobility Radeon 9000 w/ 32MB memory
	Option	"FBTexPercent"	"0" # Default is "50". "0" means that all extra memory will be reserved for EXA. If you have more graphics memory than 32, you probably shouldn't use this.
	Option	"GARTSize"	"128" # The amount of AGP Memory. "128" may be needed.
	Option	"AGPMode"	"4" # The speed of AGP Memory, the default often being "1".
	Option	"DepthBits"	"16" # Frees more memory to other uses by the expence of depth buffer.
	Option	"AccelDFS"	"true" # Speeds up the 3D Desktop
	# Next one is probably unnecessary
	Option	"EnablePageFlip" "true" # Seems to work, and in theory speeds up things. Default is "false".
EndSection
```

---

### Post by ChuckMcB on 2009-12-04
Thanks orawax.

---

### Post by nomnex on 2010-01-30
orawax, do you create a xorg.conf file on your Karmic install, and does that (really) improve the graphic rendering?

We ve got the same card, but for the memory, see [[COLOR=Red]1[/COLOR]], would you disable the lines, see [[COLOR=Red]2[/COLOR]]?

[1]
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
    Subsystem: Fujitsu Limited. Device 11fa
    Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
    Memory at f0000000 (32-bit, prefetchable) [[COLOR=Red]size=128M[/COLOR]]
    I/O ports at a000 [size=256]
    Memory at ec100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at ec120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb

```[2]
```

# The following are useful only on Mobility Radeon 9000 w/ 32MB memory
    [COLOR=Red]#[/COLOR]Option    "FBTexPercent"    "0" # Default is "50". "0" means that all extra memory will be reserved for EXA. If you have more graphics memory than 32, you probably shouldn't use this.
    [COLOR=Red]#[/COLOR]Option    "GARTSize"    "128" # The amount of AGP Memory. "128" may be needed.
    [COLOR=Red]#[/COLOR]Option    "AGPMode"    "4" # The speed of AGP Memory, the default often being "1".
    [COLOR=Red]#[/COLOR]Option    "DepthBits"    "16" # Frees more memory to other uses by the expence of depth buffer.
[COLOR=Red]#[/COLOR]Option    "AccelDFS"    "true" # Speeds up the 3D Desktop
```

---

### Post by nomnex on 2010-01-31
once again,

default config is better on my system than tweaking the xorg.conf file. I tried both settings, see above.

either it is worse, either there is no noticeable difference.

---

### Post by orawax on 2010-01-31
> **nomnex said:**
> orawax, do you create a xorg.conf file on your Karmic install, and does that (really) improve the graphic rendering?

Yes. Without the xorg.conf the system becomes totally unresponsive (hard locks) at login. I tried restarting X without the .conf just now, after reconfiguring xserver-xorg, and that's still the case. I also tried commenting out the lines you suggested, but then X becomes painfully slow and consumes 85-95% of my CPU.

EDIT: Perhaps this is a problem with only some of these cards, dunno. But with my system this tweak is absolutely necessary.

---

### Post by nomnex on 2010-02-01
Well, glad it works for you. We have got the same card, but as you say, it must be case by case (or connected to the surrounding hardware). A xorg.conf or any flavour is a no go on my system, compared to the default setting even though the Linux experience with a 128 mb ATI mobility radeon is comparable at the the beginning of the movie industry of the 19 century, in a world of HD;)

---


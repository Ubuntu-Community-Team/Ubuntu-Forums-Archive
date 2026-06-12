---
title: "sound but no video"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by cragged6 on 2007-09-03
Dell 710m, Fiesty 7.04, Intel 82852/855 graphics card.

To get this machine working with Mitsubishi data projector, I installed xserver-xorg-video-intel.

Now I get sound but no video--just a blue screen--from Totem, Mplayer, gxine and RealPlayer.

At least I think I installed x-x-v-intel...apt-get tells me I have the latest version but here is what is in xorg.conf:

```
Section "Device"
	Identifier	"Generic Video CardIntel 82852"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection
```

Should that driver be something else? Thanks for any guidance.

---

### Post by angryfirelord on 2007-09-03
Instead of saying "i810", change it to say "intel".

---

### Post by cragged6 on 2007-09-03
Tried that, restarted X. No luck.

---

### Post by angryfirelord on 2007-09-03
Driver's ok then. How are you hooking up your projector? Are you using it with another monitor? Most likely the xorg.conf isn't configured right.

See this: [http://ubuntuforums.org/archive/index.php/t-78570.html]("http://ubuntuforums.org/archive/index.php/t-78570.html")

Fortunately, Gusty is going to make xorg configuring MUCH easier.

---

### Post by cragged6 on 2007-09-03
Thanks for response AFL! (Okay if I abbreviate?)

The data projector is working with xserver-xorg-video-intel but the Totem, etc. are not.

I had used 915resolution to get my laptop monitor (1280x800) in line. Eventually got Totem, etc. to play dvd's (even a  divX (?) that is precious to me) with the codecs. But using the data projector gave wavy errors and Fn+F8 toggles went goofy.

Did a sudo apt-get install xserver-xorg-video-intel and got the projector working--so that's fine. I can project pdf's and gnuplots, etc., but now I get a blue screen--on my laptop--when playing dvd's although there is sound.

I have tried Ctrl-F2 to set gstreamer-properties, but no luck. Thanks again, Craggy.

---


---
title: "ATI Card Stubborn and Refuses to Work"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by RSVampire on 2007-05-02
Hello everybody,

I'm a new member and have started dual booting Ubuntu Fiesty and Windows XP.

I've tried everything I've read on the internet and nothing is allowing my ATI Radeon 9800 Pro to render correctly.

I've edited so no composite was enabled in my /etc/X11/xorg.conf and did the tutorial on Ubuntu's site how to get the 3-d acceleration to work. Now when I try to enable/disable the restricted drivers in the manager panel, it says "your hardware does not need any restricted drivers" and when I enable desktop effects it says "desktop effects could not be enabled". I'm totally lost now and have no clue what to do and need some help. Here are some print outs of my command line.

rsvampire@rsvampire:~$ glxinfo | grep rendering
direct rendering: No
rsvampire@rsvampire:~$ 

rsvampire@rsvampire:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2

rsvampire@rsvampire:~$

---

### Post by chickenbangbang on 2007-05-03
Hi,

I'm also a new user. I am the lucky (?) owner of an ATI Radeon 9600SE. I've just recently managed to get mine to work with direct rendering (mostly by cobbling together bits of advice found in various parts of the internet). I'll post up the relevant parts of my xorg.conf, see if this helps you in any way. If you try any of these changes, make sure you save a backup of your xorg.conf FIRST (I learnt this the hard way).

```
Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
	Load		"GLcore"
EndSection
```

Added GLCore option to the Module section.

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AQ [Radeon 9600]"
	Driver		"radeon"
	Busid		"PCI:1:0:0"
	Option		"AGPFastWrite" "yes"
	Option		"ColorTiling" "on"
	Option 		"GARTSize" "64"
	Option 		"EnablePageFlip" "True"
	Option 		"AGPMode" "2"
	Option 		"EnableDepthMoves" "True"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
EndSection
```

Added all of the options here, as well as changing the driver to 'radeon'. Some people say that AGPMode should be set to '4', but I found that setting it to 4 slowed my system to a crawl when it came to opening application windows etc - it may work for you however.

The other thing I had to do was to go into the Synaptic Package Manager. Did a search for 'fglrx', and completely removed everything except 'restricted-manager' and 'xserver-xorg-video-ati'. When I first applied the changes to my xorg.conf, it reported that direct rendering was working, but when I logged back in it had turned itself back off. Removing the fglrx stuff fixed that, though. As I'm a complete newbie, I can only assume that there's some sort of incompatibility regarding fglrx.

Once I'd done all that, I rebooted and everything seems to be working fine.

I hope these fixes work for you.

Good luck!

---

### Post by RSVampire on 2007-05-10
hmm.... nope.

all that did was break my system and I had to restore my xorg.conf file.

any other suggestions people?

---

### Post by misfitpierce on 2007-05-10
Unfortunatley I got my card working with beryl by modding the he11 outta some files. Dont even remember honestly I have a Xpress 200M ATI card. Thing is ATI is slacking on linux drivers atm so I wouldnt depend on making them work for effects. The composite outputs are bad atm from what I know. Also make sure youve gone to ati website and downloaded the appropriate up to date linux ati card driver for your card.  That may help :)

---


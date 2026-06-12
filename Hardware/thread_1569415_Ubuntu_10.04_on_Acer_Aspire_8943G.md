---
title: "Ubuntu 10.04 on Acer Aspire 8943G"
date: 2010-09-06
forum: Hardware
---

### Post by artemeas on 2010-09-06
Hello ubuntu community!

I have some problems with my laptop using ubuntu 10.04.1 (x86_64)

The main problem is my ATI Mobility Radeon HD 5850 card.

I have the latest proprietary driver from ATI homepage (10.8 ).
Everything is ok but...

1 - i have burg installed and configured (compressed the picture so it's 20 times smaller than the original one - theme coffee BUT it's veeeeerryyyy slow till it renders.. it goes from top to bottom.. and you can see how it loads.. line by line

2 - i have also Space-Sunrise Plymouth Theme installed BUT it looks somehow strange.. i mean it's kind of a game that runs on 16bit and colors are strange too.

I read in: "FoundationsTeam/LucidBootExperience"
```
Non-KMS case
In the case of hardware where we do not have a kernel mode setting driver, we will instead fallback to using ordinary framebuffer drivers which Plymouth is also capable of rendering to.

For non-x86 ports, this may be sufficient to eliminate the flickers and mode-switches; though this will require that the appropriate X drivers also be patched to support the -nr option. If not patched, a black screen will appear as the X server starts, otherwise the experience will be reasonable.

For x86 hardware with a different graphics card to the "big three", we will fallback to loading the 16-color VGA framebuffer driver. This will require a kernel change to load that driver on graphics hardware, but ensure it is last in the link/module order so that others take preference to it.

While limited in colors, a sufficiently simple plugin will be provided to give a similar experience to the current usplash.
```

I guess it's the case. There is something with KMS support on my video card (?) but my card is not the oldest one it's one of the latest. (1 gb video memory)

3 - before I installed Plymouth Theme the default boot screen looked strange too (it seamed there was something wrong with the resolution and it flickers when loading bar appears.. i mean this 5 *.. it the go black and then again colored)

I tried to disable (?) KMS by adding nomodeset to grub and burg configs - there was no difference.

Please help me bringing my ATI HD 5850 to work properly.

I don't know which information you need so please tell me which config you need.

here is my xorg.conf (at the moment it's empty :( )
after I initialized my card with aticonfig
xorg.conf looked like
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

i guess new xorg.conf was created after i added 'nomodeset' to grub/burg config

all in all video is working properly i mean visual effects are on Extra and there is absolutely no problem when ubuntu is loaded.

---

### Post by artemeas on 2010-09-12
You know what, Ubuntu and Ubuntu's Community!

All of you are handicapped persons. You can't even make a working KMS in your kernel. I used openSUSE 11.3 on my HD 5850 and had absolutely no problem, KMS worked I had no problems with configurating hardware and else..

But your custom (ubuntu) kernels suck!
You can't even help solving problems that YOU create.

It's very stupid(!) because on windows 7 my ATI lets me play all the latest games with ultra video settings without any problems.. but stupid plymouth is showing me a 16-bit image... isn't it a bit strange?!

---


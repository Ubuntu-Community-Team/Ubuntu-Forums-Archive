---
title: "Best graphics adapters/cards/chipsets?"
date: 2009-12-18
forum: Hardware
---

### Post by Ari Hyttinen on 2009-12-18
Ok, imagine I'm going to a (web) shop to buy a graphics card to be used with Ubuntu (9.04 or 9.10) PC. For simplicity's sake, let's assume it's the only (enabled) graphics adpater in the PC.

I want it to work "out of the box", ie. I put it into the PC, then I install Ubuntu, and then current software (Gnome desktop, compiz, OpenGL, games, etc) works. I'm not looking for top performance at highest resolution and quality, just something that works nicely with current OpenGL and other software.

If the drivers don't fully work "out of the box", the drivers must at least be installable through synaptic or other GUI tools, *without* command line tweaking. And even more important, the drivers must survive automatic kernel update automatically (ie. no manual re-install or anything).

What I'm looking for is a simple list of comptible and good graphics chipsets to choose from. If somebody maintains such a list, please tell me! I couldn't find one. All the lists I found were lists with all kinds of extra information about how well the cards worked and how to get them working, not what I'm looking for.

In the absence of such a list, if somebody here has a graphics card that meets the requirements above, feel free to share the graphics chipset and card model, please! :-)

Or, if I'm looking for something that just isn't possible in our current version of reality, and I'm stuck with stuff like
  [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
just tell me so... :-(

(The list isn't really for me, I'm looking for this kind of list so I don't have to become first "the list" and then "the automatic update service" for somebody else...)

---

### Post by IcarusR on 2009-12-18
Search forums this has been asked & answered before.

---

### Post by Ari Hyttinen on 2009-12-19
> **IcarusR said:**
> Search forums this has been asked & answered before.
It may have been asked and answered, but I failed at finding the answer from forums.

I mean, of course there's a lot of information, but filtering it with these forum search tools down to a useful amount is beyond me. A lot of information even in recent posts is about cards that are no longer being sold, which doesn't make it any easier. Picking one card and then searching for it works ok, but again there are a lot of cards out there, so this method is rather random and tedious. And then some of the information talks about graphics cores (or architecture versions or whatever), but it's less than trivial to get list of actual card models with a given core.

Well, apparently the somewhat contested consensus is to pick some nVidia card at desired price, search for the model to see if people have gotten it to work, buy it if it looks ok, and then follow the nVidia installation instructions for Ubuntu 8.xx hoping they still apply for Ubuntu 9.xx (probably they do apply if nobody has bothered to fix this on nVidia binary driver howto page). And then hope that things go smoothly.

---

### Post by coffeecat on 2009-12-19
You want it simple? That link is far too complicated. Go for NVIDIA - period. Go for a GeForce >= 6100, but avoid any very recent GPU.

Do you want it even more simple? Here's my 'lspci | grep VGA':

> 02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)It's the 'GeForce 8400GS' bit that's important. It 'just works' in Karmic (and in Jaunty) with the version 185 proprietary driver that I installed with System > Administration > Hardware Drivers. When you first boot up after installation you'll be running the open-source 'nv' driver which is OK but won't support 3D and compiz. All you have to do is update the system and then open the Hardware Drivers utility.

If you want to be 101% sure, I'm using the Gainward (passively-cooled) NVIDIA GeForce 8400GS 256MB DDR2 card.

But if you want a little more choice, the package information for the nvidia-glx-185 package (in Synaptic) says:

> The following GPUs are supported:
GeForce 6800 Ultra, GeForce 6800, GeForce 6800 LE, GeForce
6800 XE, GeForce 6800 XT, GeForce 6800 GT, GeForce 6800 GT,
GeForce 6800 GS, GeForce 6800 XT, GeForce 7800 GTX, GeForce
7800 GTX, GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI
, GeForce Go 7800, GeForce Go 7800 GTX, GeForce 6800 GS, GeF
orce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800
, GeForce Go 6800 Ultra, GeForce 6800, GeForce 6600 GT, GeFo
rce 6600, GeForce 6200, GeForce 6600 LE, GeForce 7800 GS, Ge
Force 6800 GS, GeForce 6800 Ultra, GeForce 6600 GT, GeForce
6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600, GeF
orce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, G
eForce Go 6600, GeForce Go 6600 GT, GeForce 6200, GeForce 65
00, GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(T
M), GeForce 6200 LE, GeForce Go 6200, GeForce Go 6400, GeFor
ce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra, Tesl
a C870, GeForce 7350 LE, GeForce 7300 LE, GeForce 7300 SE/72
00 GS, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400, Ge
Force 7500 LE, GeForce 7300 GS, GeForce 6800, GeForce 6800 L
E, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200, GeForce 6
200 A-LE, GeForce 6150, GeForce 6150 LE, GeForce 6100, GeFor
ce Go 6150, GeForce Go 6100, GeForce 7900 GTX, GeForce 7900
GT/GTO, GeForce 7900 GS, GeForce 7950 GX2, GeForce 7950 GX2,
 GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS, G
eForce Go 7900 GTX, GeForce 7600 GT, GeForce 7600 GS, GeForc
e 7900 GS, GeForce 7950 GT, GeForce 7650 GS, GeForce 7600 GT
, GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce
 7300 GT, GeForce Go 7600, GeForce Go 7600 GT, GeForce 6150S
E nForce 430, GeForce 6100 nForce 405, GeForce 6100 nForce 4
00, GeForce 6100 nForce 420, GeForce 8600 GTS, GeForce 8600
GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS, GeFo
rce 8600M GT, GeForce 8700M GT, GeForce 8400 SE, GeForce 850
0 GT, GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeF
orce 8600M GS, GeForce 8400M GT, GeForce 8400M GS, GeForce 8
400M G, GeForce 9400 GT, GeForce 7150M / nForce 630M, GeForc
e 7000M / nForce 610M, GeForce 7050 PV / NVIDIA nForce 630a,
 GeForce 7050 PV / NVIDIA nForce 630a, GeForce 7025 / NVIDIA
 nForce 630a, GeForce GTX 280, GeForce GTX 260, GeForce 8800
 GTS 512, GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS
, GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS, GeF
orce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, GeForce 96
00 GT, GeForce 9600 GS, GeForce 9800M GTS, GeForce 9800M GTS
, GeForce 9600M GT, GeForce 9600M GS, GeForce 9500M G, GeFor
ce 9300 GS, GeForce 8400 GS, GeForce 9300M GS, GeForce 7150
/ NVIDIA nForce 630i, GeForce 7100 / NVIDIA nForce 630i, GeF
orce 7050 / NVIDIA nForce 610i, GeForce 8300, GeForce 8200,
nForce 730a, GeForce 8200, GeForce 8100 / nForce 720a, Quadr
o FX 4000, Quadro FX 4500, Quadro FX Go1400, Quadro FX 3450/
4000 SDI, Quadro FX 1400, Quadro FX 4400/Quadro FX 3400, Qua
dro NVS 440, Quadro FX 540M, Quadro FX 550, Quadro FX 540, Q
uadro NVS 285, Quadro FX 5600, Quadro FX 4600, Quadro NVS 11
0M, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M, Quadro
 FX 350, Quadro NVS 210S / NVIDIA GeForce 6150LE, Quadro FX
2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quad
ro FX 1500, Quadro FX 4500 X2, Quadro FX 560, Quadro FX 370,
 Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX
 570, Quadro FX 1700, Quadro NVS 140M, Quadro NVS 130M, Quad
ro NVS 135M, Quadro FX 360M, Quadro NVS 290, Quadro FX 3700,
 Quadro FX 3600M

---

### Post by Ari Hyttinen on 2009-12-19
Excellent, thank you very much!

---


---
title: "X3100 Problems with my Compaq Presario C756ca"
date: 2008-07-21
forum: Hardware
---

### Post by deselect on 2008-07-21
Hello everybody,

This is my first post here, so please forgive the ignorance. I have been using Linux (originally Debian and now Ubuntu) for about two years now, but have not really been the type to get into some of the gritty side of things. I tend to use the system for work rather than play.

I have a new laptop now that I am having some video issues with, it seems.

I am running Hardy Heron on a Presario C756CA (which has an x3100 video card) and although I can see the wobbly effects of what I assume to be CompizFusion, I have no ripple effects or Cube and many 3d applications I run perform poorly.

When I run "compiz" in terminal, I get the following output:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Also, the xorg.conf video areas has this data (which seems shockingly sparse from my old PC setup):

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

GLXGears gives me about 1,043 FPS.

Sorry if any of what I am asking sounds terribly amateur and lame, like I said, I have mostly been using my PCs for web development. Since I found some free time in the next little bit, I would like to cross these items off my to-do list.

Thanks,
Akiva

---


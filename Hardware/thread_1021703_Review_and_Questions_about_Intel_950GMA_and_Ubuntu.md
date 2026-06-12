---
title: "Review and Questions about Intel 950GMA and Ubuntu 8.10"
date: 2008-12-25
forum: Hardware
---

### Post by Espionage724 on 2008-12-25
Ok so here is my review on the Intel 950GMA and Ubuntu 8.10

System
- 3D Acceleration out of the box
- Compiz works out of the box (decently)
- Resolutions work

Games (wine)
- Warcraft III gets 15-30FPS
- World of Warcraft (TBA)

Here is my xorg.conf file for the Intel 950GMA

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver      "intel"
	Option      "AccelMethod" "EXA"
	Option      "MigrationHeuristic" "greedy"
	Option      "ExaNoComposite"     "false"
	Option	    "TripleBuffer" "true"
	Option      "Tiling"    "true"
	Option	    "PageFlip"	"true"
EndSection
```

So here are some questions I have:

1. Is their a performance difference between XAA and EXA AccelMethods?

2. Is TripleBuffer good? I rememver that if I had it enabled on WoW in Windows, it lowered FPS (DirectX Mode)

3. Is their a performance difference between the  "inte" and the "i810" driver?

4. INTEL_BATCH=1 I heard improved performance. I ran it with glxgears and got a slight performance increase. I heard people going from 700FPS to like 1000FPS however in older versions of Ubuntu. I also heard that you can change the 1 to 4 and get more performance. Can anyone shed some light on this option?

5. [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)  This site has Intel Graphics drivers for linux. If I were to get these drivers and compile them, would I get better FPS?

6. How would I go about compiling the drivers from question #5?

7. Does Ubuntu's drivers support Hardware/Software TnL?

8. In Windows Vista, users who have an Intel 950GMA graphics card could take the 965 drivers , and install them and get basic Software TnL support along with boosted FPS. Any chance this could be done in linux?

9. Cedega says that 3D acceleration fails with the "intel" drivers from Ubuntu. Why?

10. Cedega or Wine?

11. Is there anymore xorg.conf tweaks I can perform to get better FPS?

Thanks in advance :p

---

### Post by Espionage724 on 2008-12-26
Bump.

---

### Post by Sef on 2008-12-26
> Bump

Please wait 24 hours without a post before bumping your thread.  Thank you.

---

### Post by EnderEcho on 2009-01-17
Bump. 

I want to know the answers to his questions. #5 in particular.

---

### Post by densou on 2009-01-20
> **Espionage724 said:**
> 1. Is their a performance difference between XAA and EXA AccelMethods?

EXA is known to perform better with Compiz enabled, but worse 2d than old XAA.
I think EXA is more reliable on multi-tasking.
UXA (the newer) is still unstable. Don't try it, random crashes and whatsoever.

> Is their a performance difference between the "intel" and the "i810" driver?

i810 is the old driver branch, intel (i915/1965) replaced it

> 4. INTEL_BATCH=1 Can anyone shed some light on this option?

Sound interesting. It'll give a try, lad

> If I were to get these drivers and compile them, would I get better FPS?

Don't need to compile all stuff, just add these repositories:
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
```
They contain stable backports (deb) of latest drivers ;)
I'd recommend to install 2.5.1 release.

> Does Ubuntu's drivers support Hardware/Software TnL?
Well, it's OpenGL related not about Ubuntu :p however Intel X series only has hardware TnL (except X3000).


> Is there anymore xorg.conf tweaks I can perform to get better FPS?

maybe, how much time are you ready to waste for endless tentatives ? :p

---


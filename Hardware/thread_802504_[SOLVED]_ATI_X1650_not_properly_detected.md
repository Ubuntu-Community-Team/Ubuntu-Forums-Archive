---
title: "[SOLVED] ATI X1650 not properly detected?"
date: 2008-05-21
forum: Hardware
---

### Post by indeed on 2008-05-21
Hi,

I have a PCI-E X1650 Pro which claims to have 512MB DDR2 RAM.

However, lspci reports
```
Memory at d0000000 (64-bit, prefetchable) [size=256M]

```

Catalyst control centre confirms 512MB.

Now, I'm not suffering any major performance problems (ahem) but I'm wondering whether I'm getting the most out of this card ...

Any ideas?

Edit: Actually, I should surely be getting better than 75 FPS from fgl_glxgears, no?

---

### Post by zgornel on 2008-05-22
What drivers (and version) are you using ? What does 'glxinfo' reports ?

---

### Post by indeed on 2008-05-23
Hi,

glxinfo (edited highlights) says:

```

...
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
...
client glx vendor string: SGI
client glx version string: 1.4
...
GLX version: 1.2
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7412 Release
...
```

---

### Post by zgornel on 2008-05-24
The acceleration is on and the drivers are used ... at least it seems that way. Do you have any settings in xorg.conf related to the fglrx module ? Compiz enabled ? I get ~520fps in fgl_glxgears on an X1350. As for the lspci output, something might be wrong: AMDCCLE reports its info from the bios of the card (at least it seems that way because the memory/core frequencies are the nominal values and not the real ones) Mine reports the memory correctly: ```
 Memory at d0000000 (32-bit, prefetchable) [size=128M]
``` which is 128MB 64bit DDR2. You could try GPUz (In Windows) and see what it reports.

---

### Post by indeed on 2008-05-24
The relevant sections of xorg.conf are currently ...

```
Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver      "fglrx"
#	Option		"VideoOverlay"	"off	"
#	Option		"OpenGLOverlay"	"off"
#	Option 		"TexturedVideo" "on"
#	Option		"EnablePrivateBackZ"	"yes"
#	Option		"UseInternalAGPGART"	"no"
#	Option 		"XAANoOffscreenPixmaps" "on" 
#	Option 		"UseFastTLS" "1" 
#	Option 		"BackingStore" "on" 
	BusID       "PCI:1:0:0"
EndSection

#Section "DRI"
#	Mode      0666
#EndSection

#Section "Extensions"
#	Option	    "Composite" "1"
#EndSection
```

... where the commented-out sections are options I've experimented with which have made no difference whatsoever.

My other setup is an Athlon 2.8 + GeForce 6200 (AGP) + 1 GB and I'm getting over 1500 fps from glxgears on that.
This is a Dual-Core 2.33 + X1650 Pro (PCIE) + 2GB and I only get 75 fps. Somethin' ain't right.

Thanks for your time - I'll have a tinker in windoze like you suggest, to check it's a linux specific issue.

---

### Post by indeed on 2008-05-24
Update...

Problem persists with fglrx-envy drivers.
GPUz in windoze detects/reports X1650 Pro PCI-e 512MB, all as expected.

I'm becoming convinced it's a hardware detection issue, rather than drivers/config. Then again, even if the card is detected as a 256MB X1650, it's the same chipset so surely that alone can't account for this pitiful framerate.

Edit: Also cat /proc/mtrr only says:
```
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
```
Shouldn't it mention the video ram as well?

Grrr...

---

### Post by indeed on 2008-05-24
:oops:

Erm ... it seems the main reason for the slow frame rate was that I had the "vertical refresh" slider in ATICCC set to Quality. Moving it over to Performance (always off) increased my fps in glxgears from 75 to over 5000. Who'd have thought it, eh?

In my defense I still think that there's a memory allocation problem. When I tried the radeonhd driver it said something about 512 exceeding PCI BAR or some such and so it only allocates 256. Anyone know what *that* means?

---

### Post by BigBrother84 on 2009-05-23
I have a similar problem.

[I]$ sudo lspci -v
[...]
03:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e) (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited Unknown device 0850
    Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
    Memory at c0000000 (32-bit, prefetchable) **[size=256M]**
    I/O ports at d000 [size=256]
    Memory at d3000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d2000000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] AGP version 3.0
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
[...][/I]

But Catalyst Control Center reports the correct setting:
[I]
  Graphic Card: Radeon X1650 Series
  Memory Type: DDR2
  **Memory Size: 512 MB**
  Memory Clock: 400 Mhz
  Core Clock" 600 Mhz
  Bus Type: AGP
  Bus Setting: 8x[/I] 

When I try to run compiz (enable desktop effects) I get a white screen of death. But other than that, the card works ( I can run Wolfenstein, and it handles my 1920x1200 display just fine ).


And yes.... I used EnvyNG to install the drivers.

---


---
title: "i810 Hardware Accelaration"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by gaussian on 2005-07-07
I am a complete Newbie to Ubuntu, used Mandrake/Mandriva for a year now. I picked Mandrake by accident and now would probably be ready to move Ubuntu full time (after studying some other options). But one obstacle remains: I can't get i810 3-D hardware acceleration to work (No Tuxracer for kids, no Ubuntu...). It works out of the box in Mandriva and also I tried that it works with Mepis live cd. Does anyone here have it working with Hoary with this piece of inexpensive graphics hardware?

Little info: 
Computer: Old Celeron Based HP Pavillon, with integrated i810 chip (no own memory for the card, If I understand correctly). 384Mb of Ram.

After installation (Kubuntu) everything seems to work except accelaration (e.g. glxgears: DRI no). Trying to monkey what works in Mandriva/mepis I do the following:

**in /etc/modules I load:**
agpart
intel-agp
i810fb
[B]
in etc/modprobe.d/i810fb I give the following options[/B]
options i810fb  xres=800 hsync1=32 hsync2=48 vsync1=50 vsync2=70 vram=64 bpp=16accel=1 mtrr=1

**in xorg.conf I load "glx" and have played with different options for DRI and useinternalpgpart. Results of all this tweaking: No X-server. Xorg.cong says the following**

(==) I810(0): Write-combining range (0xf8000000,0x4000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 78.9 MHz [ 0x15 0x5 0x20 ] [ 23 7 2 ]
(II) I810(0): chose watermark 0x22215000: (tab.freq 78.8)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x00000000 (pgoffset 0)
(WW) I810(0): xf86BindGARTMemory: binding of gart memory with key 2
        at offset 0x0 failed (Device or resource busy)

Fatal server error:
AddScreen/ScreenInit failed for driver 0

**If I do dmesg| grep i810 I get (actually, this from syslog):**

Jul  6 23:26:00 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Jul  6 23:26:00 localhost kernel: agpgart: Detected an Intel i810 E Chipset.
Jul  6 23:26:00 localhost kernel: agpgart: Maximum main memory to use for agp memory: 320M
Jul  6 23:26:00 localhost kernel: agpgart: AGP aperture is 64M @ 0xf8000000


Any idea what to try next? 


Saku

---

### Post by varunus on 2005-07-07
Do you have the "i915" kernel module loaded?  It provides Direct Rendering for the Intel i810 and up cards.  Also, can you post your entire xorg.conf and your entire /var/log/Xorg.0.log?

Acceleration worked out of the box for my i855 intel card in Ubuntu, so I don't know why you're having problems...hopefully we can fix them.

---

### Post by gaussian on 2005-07-07
I don't have the i915 module loaded. I'll try all you suggest tonight and post back the results (including logs and confs...). Thanks!

Saku

---

### Post by MetalMusicAddict on 2005-07-07
Everyone seems to have a problem with the "i810" drivers/chipset whatever...
I have a laptop that used 'em. Breezy seems to have fixed this. Im just playing with it now. Im still gonna look for what varunus has said.

---

### Post by gaussian on 2005-07-08
[QUOTE=varunus]Do you have the "i915" kernel module loaded?  It provides Direct Rendering for the Intel i810 and up cards.  Also, can you post your entire xorg.conf and your entire /var/log/Xorg.0.log?

Acceleration worked out of the box for my i855 intel card in Ubuntu, so I don't know why you're having problems...hopefully we can fix them.[/QUOTE]

Ok, here it comes. First I whether I was suppose load either i810 or i810fb with i915. I tried all combinations (including i915 alone). Not working.  I was also not sure whether in xorg.conf I was suppose to put i810 or i915 as the driver. The latter produced "driver not found error". The i915 related files I have on my system are
[COLOR=DarkRed]
/usr/X11R6/lib/modules/dri/i915_dri.so
/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/i915.ko
/lib/modules/2.6.10-5-686/kernel/drivers/char/drm/i915.ko
[/COLOR]

I noticed with lsmod that vesafb gets always loaded. Could this be part of the problem?  I am attaching my xorg.conf and Xorg.0.log in this post (Xorg.0.log is split into two halfs).
Any ideas what to do next? And thanks for all the help!

Saku

---

### Post by varunus on 2005-07-09
OK, looking at your xorg.conf, I can see two problems.  I don't know if you added these yourself, or if the Hoary install did it, but I would recommend doing the following:

In the modules section, you have many things commented out.  The most important line here is the

```
#  Load "dri"
```

This stops you from loading hardware acceleration modules.  I would recommend uncommenting <I>everything</I> in the modules section, as it works for me and I have acceleration.

Change Module to:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection
```

The second problem is in the Device section.
```

Section "Device"
 Identifier "device1"
    VendorName "Intel Corp."
    BoardName "Intel 810"
    Driver "i810"
    VideoRam 32768
    Option "DPMS"
    Option "XaaNoPixmapCache"
    Option "DRI" "true"
    Option "NoAccel" "false"
    Option "UseInternalAGPGART" "yes"
EndSection
```

First of all, get rid of the "UseInternalAGPGART" so it will use the kernel module.  Second, get rid of the "XaaNoPixmap Cache" Option, as it disables some hardware acceleration.

Try that, and good luck.  If it doesn't work, I can send you an exact copy of my xorg.conf, which works with hardware acceleration, and you can try that.

Enjoy.

---

### Post by gaussian on 2005-07-10
[QUOTE=varunus]OK, looking at your xorg.conf, I can see two problems.  I don't know if you added these yourself, or if the Hoary install did it, but I would recommend doing the following:

In the modules section, you have many things commented out.  The most important line here is the

```
#  Load "dri"
```

This stops you from loading hardware acceleration modules.  I would recommend uncommenting <I>everything</I> in the modules section, as it works for me and I have acceleration.

Change Module to:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection
```

The second problem is in the Device section.
```

Section "Device"
 Identifier "device1"
    VendorName "Intel Corp."
    BoardName "Intel 810"
    Driver "i810"
    VideoRam 32768
    Option "DPMS"
    Option "XaaNoPixmapCache"
    Option "DRI" "true"
    Option "NoAccel" "false"
    Option "UseInternalAGPGART" "yes"
EndSection
```

First of all, get rid of the "UseInternalAGPGART" so it will use the kernel module.  Second, get rid of the "XaaNoPixmap Cache" Option, as it disables some hardware acceleration.

Try that, and good luck.  If it doesn't work, I can send you an exact copy of my xorg.conf, which works with hardware acceleration, and you can try that.

Enjoy.[/QUOTE]
 Thanks for the help. But still no result. If you could post your xorg.conf (parts of /etc/modules and /etc/modprobe.d/ could also be helpful) that would be great. 

Thanks,

Saku

---

### Post by flankk on 2005-07-10
I have seen this topic overlooked so many times and it disappoints me.  Intel integrated chips comprise a huge part of the integrated video market.  I have an Intel 845G chipset, and I've gone through much havoc with linux support.  Now, there are newer drivers, and all you really need is the newest i915 cvs snapshot from the DRI project, as varunus stated.

---

### Post by gaussian on 2005-07-10
Thanks Flankk. I did not understand originally that I needed to get the newest i1915 drivers, I thought I needed to load the one driver called i915 already on the system.  Hopefully this gets it working. I'll report back in few days (when I have time to do this) on whether it was a success or not.

Saku

---

### Post by gaussian on 2005-07-15
Ok, the end result still is no hardware accelaration and that I am bidding on ebay for a used NVIDIA card  :) There just seems to be something particular with this machine/chipset/motherboard that makes it very ubunty imcompatible (i810e) or maybe it is just me. 

Anyway, I downloaded the dri-snapshot binaries (I don't know why they are called binaries, since you still compile at least some of them) and after installing bunch of libraries/header files they compiled ok. One word of advice for someone trying this: it seems that they don't compile with the 386-kernel, but do compile with 686-kernel (like it also saids on this thread [http://ubuntuforums.org/showthread.php?t=7200&highlight=dri+snapshot](http://ubuntuforums.org/showthread.php?t=7200&highlight=dri+snapshot)) 

I tried all the possible combinations of tweaking with modules to load and lines to add/delete to xorg.conf. End result: some times X did not load, sometimes it loaded, but always with DRI and the /var/log/Xorg.0.log had some error message (different depending on the setup) about agpgart and no DRI. 

Then I did really stupid stuff and tried to upgrade to breezy. End result: X is broken, but not broken enough to not to give me agpgart related error messages (needless to say, it is ok for breezy to have  broken X, I am absolutely not complaining about that). Anyway, I will do a new hoary install (luckily Ubuntu is still the playground, I have a perfectly working Mandriva) and wait for luck in ebay in getting a real non-integrated (unfortunately PCI, not AGP) graphics card.


Thanks for all who helped.

Saku

---


---
title: "SiS Video Driver... again (Sis 662 on Intel D201GLY2, Mirage *, and more)"
date: 2008-11-01
forum: Hardware
---

### Post by tuneable on 2008-11-01
I knew it (but I forgot)! Halloween seems to have revived an old demon, packaged as the SiS video driver for xorg in Ubuntu 8.10. It is not(!) Ubuntu's fault, but be warned before you upgrade.

I was seriously happy when some smart people figured out a way to patch the open-sourced drivers for the SiS 662 chip (on a Intel D201GLY2 mainboard) and it worked for about as long as the Xorg version was not changed in Ubuntu.

[[link 1]("http://ubuntuforums.org/showthread.php?p=4981081#post4981081")] original thread on the problem, I think it covers Ubuntu 7.10-8.04
[[link 2]("http://ubuntuforums.org/showthread.php?t=728147")] a second solution(!) thread, worked for 8.04
[[link 3]("http://ubuntuforums.org/showthread.php?t=930930")] current problem described well by Master One. I obviously missed his warning.

Symptoms: A noisy banding that makes your screen unreadable. 
The quick fix: set your /etc/X11/xorg.conf to use the "vesa" driver, e.g. by adding a line to the device section:
```
Section "Device"
         Identifier      "Configured Video Device"
        **driver          "vesa"**
EndSection

```

Using the vesa driver removes the banding. Nice! But it eats CPU and gives you window response that resembles slide-animations on a famous presentation app - dead slow. And no 2d acceleration, forget about watching video.

I hope the same (or other) smart people can battle this demon once more, and figure out a way to patch the SiS driver. If I missed an important driver update from Intel or SiS (one can still hope they care, right?), please let it be known in the forum too.

Thanks!

---

### Post by tuneable on 2008-11-02
There is some success possible using the "sisfb" module to get rid of the noise:

[[link 1]("http://ubuntuforums.org/showpost.php?p=6067968&postcount=7")] sisfb solution?

It did not work for me on a d201gly2. 


I found a temporary workaround that seems to be slightly better than the slow vesa driver: The glitches seem much less visible when I use a 800x600 resolution and 75Hz refresh rate. The glitches do not disappear completely (so YMMV).

---

### Post by mgol on 2008-11-02
.

---

### Post by mgol on 2008-11-02
At mine, vesa driver doesn't eat all CPU, I have system CPU usage at about 25% still (CPU AMD Sempron Mobile 3000+). My xorg is though bigger:
```

Section "Device"
	Identifier "Generic Video Card"
	Boardname "sis"
	Busid "PCI:1:0:0"
	Driver "vesa"
	Screen 0
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	Vendorname "Generic"
	Modelname "Flat Panel 1280x800"
	HorizSync 31.5-90
	VertRefresh 60
	Modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -Vsync -Hsync
	Modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +Hsync +Vsync
	Modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -Vsync -Hsync
	Modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -Hsync +Vsync
	Modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +Hsync +Vsync
	Modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +Hsync +Vsync
	Modeline "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -Hsync +Vsync
	Modeline "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -Hsync +Vsync
	Modeline "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -Hsync +Vsync
	Gamma 1.0
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Generic Video Card"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x800@60" "640x480@60" "800x600@60" "1024x768@60" "1280x1024@60" "1600x1200@60" "1792x1344@60" "1856x1392@60" "1920x1440@60"
	EndSubSection
EndSection

```
Those modelines can be obtained by running:
```
gtf <resolution.x> <resolution.y> <vertical refresh rate>
```
For my notebook, it was:
```

$ gtf 1280 800 60

  # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

```
"1280x800_60.00" part is only a name, the only important thing about it is that it should be repeated in exactly the same way in "modeline" and "modes" and that it should not replace original vesa aliases (such as "1024x768" etc.). The best way is just to change "_" into "@".

I cannot obtain true 1280x800, though - I get 1280x768; it seems that vesa doesn't support 1280x800 (but I can be wrong about it).

Anyway, waiting for the fix in [the Launchpad thread]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/264769")...

---

### Post by tuneable on 2008-11-02
Thanks for the link, i will keep an eye on that one :)

On the CPU usage I have to add the CPU stays relatively low if nothing is moving. Add any animation (websites with flash, videos) and things slow down with high CPU usage (more than I was used to).

I do get 1280x1024 on the vesa driver on my system with pretty much no changes to the xorg.conf (no modlines needed, no extras in the monitor section).

Cheers

---


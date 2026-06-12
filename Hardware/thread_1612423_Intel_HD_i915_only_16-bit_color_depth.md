---
title: "Intel HD i915 only 16-bit color depth?"
date: 2010-11-03
forum: Hardware
---

### Post by akvik on 2010-11-03
Hi,

I'm using 10.10 64-bit on a HP Elitebook 2540p which has an Intel HD graphics card.

It seems the display only shows 16-bit color, or in some way create jagged color tones - does anyone know how to fix this? Is it a common problem? The xorg log (see below) seems to indicate that the display is in 24-bit, but surely it is not - see attached screenshot of my desktop to see what I mean.

I am not using my own xorg.conf - using the new conf directly from default 10.10 install. Compiz works perfect.

From lspci -vv:
```


00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 7008
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 5058 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0c00c  Data: 41a9
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a4] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: i915
	Kernel modules: i915

```

And here is the output from cat /var/log/Xorg.0.log | grep 'intel(0)'

```

[  7800.356] (II) intel(0): Creating default Display subsection in Screen section
[  7800.356] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  7800.356] (==) intel(0): RGB weight 888
[  7800.356] (==) intel(0): Default visual is TrueColor
[  7800.356] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[  7800.356] (--) intel(0): Chipset: "Arrandale"
[  7800.356] (==) intel(0): video overlay key set to 0x101fe
[  7800.373] (II) intel(0): Output VGA1 has no monitor section
[  7800.401] (II) intel(0): Output DP1 has no monitor section
[  7800.410] (II) intel(0): Output HDMI1 has no monitor section
[  7800.415] (II) intel(0): Output DP2 has no monitor section
[  7800.425] (II) intel(0): Output HDMI2 has no monitor section
[  7800.430] (II) intel(0): Output DP3 has no monitor section
[  7800.447] (II) intel(0): EDID for output VGA1
[  7800.474] (II) intel(0): EDID for output DP1
[  7800.474] (II) intel(0): Manufacturer: SEC  Model: 4b41  Serial#: 0
[  7800.474] (II) intel(0): Year: 2009  Week: 0
[  7800.475] (II) intel(0): EDID Version: 1.4
[  7800.475] (II) intel(0): Digital Display Input
[  7800.475] (II) intel(0): Undefined color depth
[  7800.475] (II) intel(0): Digital interface is undefined
[  7800.475] (II) intel(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[  7800.475] (II) intel(0): Gamma: 2.20
[  7800.475] (II) intel(0): No DPMS capabilities specified
[  7800.475] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  7800.475] (II) intel(0): First detailed timing is preferred mode
[  7800.475] (II) intel(0): Preferred mode is native pixel format and refresh rate
[  7800.475] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[  7800.475] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[  7800.475] (II) intel(0): Manufacturer's mask: 0
[  7800.475] (II) intel(0): Supported detailed timing:
[  7800.475] (II) intel(0): clock: 69.3 MHz   Image Size:  261 x 163 mm
[  7800.475] (II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1353 h_border: 0
[  7800.475] (II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 854 v_border: 0
[  7800.475] (II) intel(0): Supported detailed timing:
[  7800.475] (II) intel(0): clock: 46.2 MHz   Image Size:  261 x 163 mm
[  7800.475] (II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1353 h_border: 0
[  7800.475] (II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 854 v_border: 0
[  7800.475] (II) intel(0): Unknown vendor-specific block 2
[  7800.475] (II) intel(0): EDID (in hex):
[  7800.475] (II) intel(0): 	00ffffffffffff004ca3414b00000000
[  7800.475] (II) intel(0): 	00130104801a10780a87f594574f8c27
[  7800.475] (II) intel(0): 	27505400000001010101010101010101
[  7800.475] (II) intel(0): 	010101010101121b0049502036301030
[  7800.475] (II) intel(0): 	130005a3100000190c12004950203630
[  7800.475] (II) intel(0): 	1030130005a310000019000000000000
[  7800.475] (II) intel(0): 	00000000000000000000000000000002
[  7800.475] (II) intel(0): 	000c3fd60a3c641a0e236400000000b6
[  7800.475] (II) intel(0): Printing probed modes for output DP1
[  7800.475] (II) intel(0): Modeline "1280x800"x60.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7800.475] (II) intel(0): Modeline "1280x800"x40.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7800.484] (II) intel(0): EDID for output HDMI1
[  7800.489] (II) intel(0): EDID for output DP2
[  7800.499] (II) intel(0): EDID for output HDMI2
[  7800.504] (II) intel(0): EDID for output DP3
[  7800.504] (II) intel(0): Output VGA1 disconnected
[  7800.504] (II) intel(0): Output DP1 connected
[  7800.504] (II) intel(0): Output HDMI1 disconnected
[  7800.504] (II) intel(0): Output DP2 disconnected
[  7800.504] (II) intel(0): Output HDMI2 disconnected
[  7800.504] (II) intel(0): Output DP3 disconnected
[  7800.504] (II) intel(0): Using exact sizes for initial modes
[  7800.504] (II) intel(0): Output DP1 using initial mode 1280x800
[  7800.504] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  7800.504] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[  7800.504] (==) intel(0): DPI set to (96, 96)
[  7800.504] (II) intel(0): [DRI2] Setup complete
[  7800.504] (II) intel(0): [DRI2]   DRI driver: i965
[  7800.504] (**) intel(0): Tiling enabled
[  7800.504] (**) intel(0): SwapBuffers wait enabled
[  7800.504] (==) intel(0): VideoRam: 262144 KB
[  7800.504] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[  7800.511] (==) intel(0): Backing store disabled
[  7800.511] (==) intel(0): Silken mouse enabled
[  7800.511] (II) intel(0): Initializing HW Cursor
[  7800.550] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  7800.550] (==) intel(0): DPMS enabled
[  7800.550] (==) intel(0): Intel XvMC decoder enabled
[  7800.550] (II) intel(0): Set up textured video
[  7800.550] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  7800.550] (II) intel(0): direct rendering: DRI2 Enabled
[  7800.557] (II) intel(0): Setting screen physical size to 338 x 211
[  7802.442] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7802.442] (II) intel(0): Printing DDC gathered Modelines:
[  7802.442] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7802.442] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7802.517] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7802.517] (II) intel(0): Printing DDC gathered Modelines:
[  7802.517] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7802.517] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7802.591] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7802.591] (II) intel(0): Printing DDC gathered Modelines:
[  7802.591] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7802.591] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7802.665] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7802.665] (II) intel(0): Printing DDC gathered Modelines:
[  7802.665] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7802.665] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7811.667] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7811.667] (II) intel(0): Printing DDC gathered Modelines:
[  7811.667] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7811.667] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7811.743] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7811.743] (II) intel(0): Printing DDC gathered Modelines:
[  7811.743] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7811.743] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7811.819] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7811.819] (II) intel(0): Printing DDC gathered Modelines:
[  7811.819] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7811.819] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7812.369] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7812.369] (II) intel(0): Printing DDC gathered Modelines:
[  7812.369] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7812.369] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)
[  7816.767] (II) intel(0): EDID vendor "SEC", prod id 19265
[  7816.767] (II) intel(0): Printing DDC gathered Modelines:
[  7816.767] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (51.2 kHz)
[  7816.767] (II) intel(0): Modeline "1280x800"x0.0   46.20  1280 1296 1344 1353  800 801 804 854 -hsync -vsync (34.1 kHz)

```

---

### Post by syscomp on 2010-11-06
yea .. same with me .. any solution for this

---

### Post by nulldozer on 2010-11-09
Same here. Anyone?

---

### Post by krazyd on 2010-11-09
i'm not sure what we're supposed to be seeing in that screenshot..

---

### Post by akvik on 2010-11-10
Fair enough, 

the screenshot is actually not very illustrative - a better example are the menus and the tones in them. They are "jagged" and not smooth. Svg images with tonality as well.

---

### Post by akvik on 2010-11-11
Here is a screenshot that might work better to illustrate the problem - check the tonality in the Lightning event, it is meant to be supersmooth, but not here.

EDIT: aha, I checked the screenshot on a different computer, and then it doesn't show at all... Even on external monitors on the 2540p it doesn't show.

---

### Post by krazyd on 2010-11-11
> **akvik said:**
> Here is a screenshot that might work better to illustrate the problem - check the tonality in the Lightning event, it is meant to be supersmooth, but not here.

EDIT: aha, I checked the screenshot on a different computer, and then it doesn't show at all... Even on external monitors on the 2540p it doesn't show.

Weird!

The EDID provided by your monitor says this:
```
[  7800.474] (II) intel(0): EDID for output DP1
[  7800.474] (II) intel(0): Manufacturer: SEC  Model: 4b41  Serial#: 0
[  7800.474] (II) intel(0): Year: 2009  Week: 0
[  7800.475] (II) intel(0): EDID Version: 1.4
[  7800.475] (II) intel(0): Digital Display Input
**[  7800.475] (II) intel(0): Undefined color depth**

```

Mine says this:

```
[    10.519] (II) intel(0): EDID for output DP1
[    10.519] (II) intel(0): Manufacturer: AUO  Model: 123e  Serial#: 0
[    10.519] (II) intel(0): Year: 2009  Week: 0
[    10.519] (II) intel(0): EDID Version: 1.4
[    10.519] (II) intel(0): Digital Display Input
**[    10.519] (II) intel(0): 6 bits per channel**
```

So a bad EDID could potentially be the issue. I would try:

1. Reading the [man pages for xorg.conf]("http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html") (scroll down to the SCREEN SECTION heading).
2. Putting a configuration file in your xorg.conf.d/ and adding a section like:
```
           Section "Screen"
               Identifier "name"
               Device     "devid"
               Monitor    "monid"
               entries
               ...
               SubSection "Display"
                  entries
                  ...
               EndSubSection
               ...
           EndSection
```

Here you should set the DefaultDepth option to 24. The man page says:
```
       DefaultDepth  depth
              specifies which color depth the server should  use  by  default.
              The -depth command line option can be used to override this.  If
              neither is specified, [B]the default depth is driver-specific,  but
              in most cases is 8.[/B]

```

So it seems like this could be causing the effect you're seeing. 

Note that you shouldn't have to create a whole /etc/X11/xorg.conf file, just a single file with a "Screen" section in your /usr/share/X11/xorg.conf.d folder ([thinkwiki has an example]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d")).

Unfortunately, I don't have much experience tweaking settings in xorg.conf.d. Let us know how you go!

EDIT: you might also want to report this as a bug on Launchpad. I believe there is a list of known badly behaved hardware (like your monitor) which can have the bit-depth forced.

---

### Post by akvik on 2010-11-13
Thanks,

The second line at the top says: 
```

[  7800.356] (==) intel(0): Depth 24, (--) framebuffer bpp 32

```

so it's hard to know what applies.

the new xorg config system is confusing - how can I make sure that the identifiers match the rest of the config, such as Monitor "monid" and so on? 

Will try it and hope for the best.

---

### Post by akvik on 2010-11-13
Hi,

I've now tried with:
```
sudo Xorg -configure
```

and started X with the new xorg.conf:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "dri"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

X loads with the new xorg.conf file:
```
--> more /var/log/Xorg.0.log | grep xorg.conf
[     5.632] (==) Using config file: "/etc/X11/xorg.conf"
[     5.632] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
```

Same result as before:
```
--> more /var/log/Xorg.0.log | grep [D/d]epth
[     5.655] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.767] (II) intel(0): Undefined color depth
[     5.790] (==) Depth 24 pixmap format is 32 bpp

```

I'm starting to suspect it's not X related but the laptop screen itself somehow, since the external monitors work as they are supposed to.

---

### Post by krazyd on 2010-11-14
> **akvik said:**
> I'm starting to suspect it's not X related but the laptop screen itself somehow, since the external monitors work as they are supposed to.

well that's where the EDID resides - in the monitor, so I think it is the laptop screen too. however this info can be over-ridden in xorg.conf.

Try formatting the screen section of your xorg.conf without the Display subsection, instead just use DefaultDepth. Like this:
```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
EndSection
```

Does that make a difference?

---

### Post by akvik on 2010-11-15
Thanks,

with the new changes in the xorg.conf, I get this, which is the same as before:
```


--> more /var/log/Xorg.0.log | grep [D/d]epth
	"Screen0" for depth/fbbpp 24/32
[     5.234] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.561] (II) intel(0): Undefined color depth
[     5.582] (==) Depth 24 pixmap format is 32 bpp

```

---

### Post by krazyd on 2010-11-15
I think you should file a bug report and try asking around on IRC.. someone there will know more about the new X configuration system.

---

### Post by stueble on 2011-02-02
Hi. Any new results on this topic? I also have a 2540p and noticed a related problem:

Right after booting, the colors look ok. But after a suspend/resume the color space seems to be reduced, similar to the figures uploaded here. Restarting X does not help - the color space keeps reduced. Only a reboot helps.

However, I am not convinced that this is a 16bit problem. When I explicitly set 16 bot color in xorg.conf after a suspend/resume, colors look ok. Restarting with 24bit again looks ugly. Thus, I have the feeling that after suspend/resume, only the 24bit color mode is broken and set to 8bit color table.

Opinions?

Best regards,
Chris

---

### Post by akvik on 2011-02-03
Interesting, 

Will check if this applies to my setup as well. I also don't think it's a color space problem, since external displays work just fine. Something else is at play. Seem to remember a post about this problem on Windows as well, on the 2540p.

---

### Post by stueble on 2011-02-04
Hi again,

I have to correct myself. After suspend/resume, the 24bit color mode seems to be broken, but the result is not 8 but 16bit. I tried a color test after resume and the colors look like the second picture ([http://www.cywarp.com/faqtruecolortest.htm](http://www.cywarp.com/faqtruecolortest.htm))

Best regards,
Chris

---


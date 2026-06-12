---
title: "Monitor dot clock problems!"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by mattlach on 2006-04-05
I posted a thread in the main ubuntu forum but I have since come to realize that it belongs here.

I am having a terrible time getting X to display at my flatpanels natural resolution (1920x1600)

I have been playing around with xorg.conf, the relevant settings are below
```

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "DPMS"
        Option "HorizSync"   "DFP-0:30-81"         Option "VertRefresh" "DFP-0:56-76"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-76
        **Modeline        "DELL1920"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync**
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24

        Subsection "Display"
                Depth           8
                Modes           "1920x1200" "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200" "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
                ViewPort        0 0
        EndSubSection
EndSection

```

From Xorg.log it appears the problem is that it for some reason thinks my monitor cant have a dot clock above 165, which is odd, since I have been running it at higher than that in other installs of X in the past.

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "HorizSync" "DFP-0:30-81"
(**) NVIDIA(0): Option "VertRefresh" "DFP-0:56-76"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xE8000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce 6800 GT
(--) NVIDIA(0): VideoBIOS: 05.40.02.15.01
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(II) NVIDIA(0): Connected display device(s): DFP-0
**(--) NVIDIA(0): DFP-0: maximum pixel clock: 165 MHz**
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-81.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 56.00-76.00 Hz
**(II) NVIDIA(0): Clock range:  12.00 to 165.00 MHz**
**(II) NVIDIA(0): Not using mode "DELL1920" (bad mode clock/interlace/doublescan)**
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
...
and so forth

```

For my natural resolution I need a Dot Clock of 193Mhz or so, but for some reason it's convinced itself that the max iss 165Mhz.  Does anyone know why?  Is there any way I can override this?

I am using the version of the closed source nvidia drivers that are in apt-get, and it loads fine..

Any ideas?

Much appreciated,
Matt

---

### Post by dermotti on 2006-04-05
Make a backup of your xorg.conf and run
[B]
sudo dpkg-reconfigure xserver-xorg[/B]

It has resolved alot of my xorg issues in the past...

---

### Post by mattlach on 2006-04-05
[QUOTE=dermotti]Make a backup of your xorg.conf and run
[B]
sudo dpkg-reconfigure xserver-xorg[/B]

It has resolved alot of my xorg issues in the past...[/QUOTE]

Thanks,  Tried that with no success :(

It almost seems as if X is reading the wrong dto clock information from the monitor...  Is there a way to override and specify the exact dot clock the monitor has?

---

### Post by mattlach on 2006-04-05
*deleted*

---

### Post by mattlach on 2006-04-06
In desperation I booted up in windows and took a look at powerstrip to get my windows display details.

[IMG]https://home.comcast.net/~mkarlsson/ubuntuforums/timings.jpg[/IMG]

I used this info to manually write the following modeline:

```

Modeline "1920x1200@60" 153.562 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync

```

And it still didn't work.

My Xorg.log says:
```

(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-81.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 56.00-76.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 165.00 MHz
(II) NVIDIA(0): Not using mode "1920x1200@60" (width too large for virtual size)

```

I'm fairly certain that modeline is correct, but I have no idea what "width too large for virtual size" means...   Anyone?

I'm starting to think there may be a bug in X or the nvidia driver or both...  I am at my wits end...

Anyone have any ideas given this new information?

Much appreciated,
Matt

---

### Post by mattlach on 2006-04-06
[QUOTE=mattlach]
I'm fairly certain that modeline is correct, but I have no idea what "width too large for virtual size" means...   Anyone?

I'm starting to think there may be a bug in X or the nvidia driver or both...  I am at my wits end...

Anyone have any ideas given this new information?

Much appreciated,
Matt[/QUOTE]

So I read the Xorg manual, and found how to add the Virtual string to my display section as follows:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	
	Subsection "Display"
		Depth		8
		Virtual		1920 1200
		Modes		"1920x1200" "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Virtual		1920 1200
		Modes		"1920x1200" "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Virtual		1920 1200
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
		#ViewPort	0 0
	EndSubSection
EndSection

```

So now instead my monitor gives me a virtual screen of 1920x1200, but its still displaying at a physical resolution of 1600x1200, and I have to pan back and forth in the letterbox in th emiddle of my screen.

Heres the kicker though.  Apparently finally my modeline was accepted

Xorg.log
```

(**) NVIDIA(0): Validated modes for display device DFP-0:
(**) NVIDIA(0):      Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
**(**) NVIDIA(0):      Mode "1920x1200@60": 153.6 MHz, 73.8 kHz, 59.8 Hz**
(**) NVIDIA(0):      Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
...
and so on

```

But now that it is finally accepted, I cant switch to it using ctrl-alt+ or ctrl-alt- and though its in the available resolutions menu, all that does is give me the virtual resolution, which displays inside the 1600x1200 window...

This is driving me nuts.   Any ideas?  (sooner or later somone who has gone through this ordeal mus come upon this thread...  :p  )

---

### Post by mattlach on 2006-04-06
SUCESS!

Turns out I was being silly.

I did all the difficult stuff (writing modelines, etc) correctly, but I messed up on the easy part.

Under my displays I had configured it to use 1920x1200, instead of setting it to use the name I had given my custom modeline!

---


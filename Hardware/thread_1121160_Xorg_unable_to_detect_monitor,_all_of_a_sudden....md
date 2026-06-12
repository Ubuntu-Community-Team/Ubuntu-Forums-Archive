---
title: "Xorg unable to detect monitor, all of a sudden..."
date: 2009-04-09
forum: Hardware
---

### Post by Mochabuntoo on 2009-04-09
Hi,

I've recently developed an issue where X seems completely unable to detect/decipher my Viewsonic VX2235WM's EDID, effectively leaving me with a resolution of 640x480. Xorg.0.log indicates 
'Unable to get display device DFP-0's EDID; cannot compute DPI from DFP-0's EDID.'

This is an issue to has seemingly appears out of the blue, simply booted into Ubuntu and found myself in low graphics mode.

I'm reliatvely new to the whole Linux thing but I've googled around, tried a few fixes, even tried a complete re-install of Ubuntu to no avail, still getting the same error message.

I've tried to convince X to forget about using an EDID and simply defining what resolutions/refresh rates my monitor is capable of in xorg.conf, but it doesn't seem to like the mode I set and goes straight back to nvidia's autodetected 640x480 glory. (Using a GeForce 8800GTS with latest nVidia drivers (180))

Apparently this issue can be worked around by getting hold of a VGA>DVI serial adapter and using that, but... I don't have one to try.

Any ideas?

---

### Post by Mochabuntoo on 2009-04-09
Well, I've managed to at least get my monitor to display a higher resolution with a little tweaking of xorg.conf.

This is using the VESA drivers, will attempt the following config with nVidia drivers shortly.

For those interested, this xorg.conf was built from a failsafe.

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"ViewSonic"
	ModelName	"VX2235wm"
	HorizSync	30-70
	VertRefresh	56-85
	Option		"dpms"
	ModeLine "1024x768@60" 65.00 1024 1048 1184 1344 768 771 777 806 -HSync -VSync
	ModeLine "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 +HSync +VSync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
	Option		"UseEdid" "False"
		SubSection	"Display"
		Depth 		24
		Modes		"1680x1050@60" "1024x768@60"
		EndSubSection
EndSection
```

Good to be back in 1680x1050, despite the somewhat slow performance!

---

### Post by Mochabuntoo on 2009-04-09
Dear diary,

After installing nVidia driver 180, back to 640x480 resolution.

From xorg.0.log;

```
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050@60"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768@60"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
```

So the nvidia drivers drivers don't seem to like the modes VESA does... Will go see what I can find from the nVidia readme to see if there is a work around.

Any input welcome... :)

---

### Post by collinp on 2009-04-09
As a first step, try running
```
sudo nvidia-xconfig
```and see if that helps anything.

---

### Post by Mochabuntoo on 2009-04-09
Hi Hellow,

Thanks for the input, have tried that in the past to no avail. Tried it again for yuks, still throwing the same message.

Need to get nVidia drivers to validate the modes that I'm setting somehow I think.

---

### Post by collinp on 2009-04-09
Not sure if this will work, but:

[LIST=1]
[*]Remove the 180 driver and run "sudo dpkg-reconfigure xserver-xorg"
[*]Reboot
[*]Reinstall 180 driver and run "sudo nvidia-xconfig"
[*]Reboot
[/LIST]
Report back if that fixes it.

---

### Post by Mochabuntoo on 2009-04-09
Yup, thats a no-go either.

I officially give up, just going to use VESA drivers. Thanks anyway!

---

### Post by ReenenLaurie on 2009-04-23
No!  Please don't give up.  I have exactly the same issue, but I am still going around in 640x480 (admittedly, I've made the "panning" to 1600x1200, but it makes for an interesting browsing experience).

But I could be going back to vesa for now.  How exactly did you do that?

---

### Post by ReenenLaurie on 2009-04-23
I got mine to work!  (I have a MSI geforce fx 5500 agp)

Basically... (in my case) after nvidia, linux would recognise my monitor, and would go into crazy conservative mode.

All I had to do was add Refreshrates to the MONITOR part of xorg.conf.

So my xorg.conf (/etc/X11) looks like this:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31.5 - 90.0
        VertRefresh 60.0 - 60.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        # Disable       "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        # Option "UseEDID" "False"
EndSection

```

I doubt the # Disable "dri2" is necessary, and on some forums I saw people suggesting that you disable UseEDID.  Don't think either is necessary.

Looking at your logs (System -> Administration -> System Log -> Xorg.0.log) could give you a hint if the error is similar to ours. (referring to Unable to get display device DFP-0's EDID / Unable to get display device CRT-0's EDID)

---

### Post by Mochabuntoo on 2009-04-26
Hey, sorry I've been away.

Great job on gettings your problem sorted out. I tried your fix in the past and it didn't work for me, but I did eventually manage to fix my issue in the end. :)

I dual-boot XP (slowly weening myself off it) so, I downloaded  [EDID Viewer.]("http://www.freewarehome.com/index.html?http%3A//www.freewarehome.com/bx/index.php%3Faction%3Dvthread%26forum%3D9%26topic%3D6579")

I then ran the program, exporting my monitor's EDID data into a .raw file. I then copied that over to my Ubuntu install, and forced my xorg.conf to use the EDID.raw file as opposed to actually trying to grab it from monitor itself.

I'm on my XP install at the moment (haven't used it in around 9 days, haha) but I'll update later with the syntax required to make xorg behave.

---

### Post by Mochabuntoo on 2009-04-28
For those interested, my xorg.conf with custom EDID;

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    Option         "NoLogo" "True"
    Option         "UseDisplayDevice" "DFP-0"
    Option         "CustomEDID" "DFP-0:/etc/X11/edid.raw"
EndSection
```

Ensure that HorizSync / VertRefresh values match up to those of your monitor, or you risk breaking things. Check your monitors specifications.

Hope that helps someone out there. :D

---

### Post by stepkas on 2012-08-11
thx, man, you're the best. Works perfect!

---


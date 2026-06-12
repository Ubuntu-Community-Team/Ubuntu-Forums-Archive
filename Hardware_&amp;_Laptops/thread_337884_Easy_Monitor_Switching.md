---
title: "Easy Monitor Switching?"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by Jheric on 2007-01-13
I finally made the switch to Ubuntu on my Laptop. It's been an *AWESOME* experience so far (save a couple issues like wireless). I'm not new to linux, but this is my first laptop.

**This is my question:**

While on windows I was able to use the VGA port on the back of my Laptop (Acer Aspire 5100) when I'm at home to hook up to my 19" widescreen LCD. Here's the deal tho. I'm hooked on Beryl, so I don't care about Big Desktop or the like (3d stopped working).* All I want to do is have an easy way to switch to it as my primary monitor while at home.* Is there an easy way to do this  without messing up my settings for when I'm out and about?

Right now, if I hook up my monitor, it simply displays a clone that is the wrong resolution with  100-200 pixels of dead space on the left side. 

Here's my xorg (some of it):

> Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"

EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection

---

### Post by Jheric on 2007-01-14
Is this really that difficult to do?

I've searched the forums, but all I can find are guides for dual monitor support. Is anyone else simply making a sencond monitor the primary display for their laptop?

-Garrett

---

### Post by oudalrich on 2007-03-02
I've had the same problem and managed to work it out. While looking for a solution, I came across your post. In case you're still here, here's what should work (make sure your external display is plugged in):

```

sudo aticonfig --dtop=clone
sudo aticonfig --mode2=1680x1050,1024x768

```

Of course, you'll have to adjust the resolutions to whatever your external display can handle. I put the lower resolution in for safety, the higher one will be used.

Now restart your X session (by typing CTRL-ALT-DEL) or restart you computer (AFAIK, with current versions of X there's no way of changing resolutions on the fly). You should see the external monitor run at its native resolution. The laptop LCD should clone whatever fits into its lower resolution. If you move the cursor around, it will scroll around the desktop. You can turn the internal LCD off by doing:

```

aticonfig --enable-monitor=crt1

```

And to turn it back on:

```

aticonfig --enable-monitor=lvds,crt1

```

If you boot your laptop without the external display attached, X will run at your laptop's internal resolution.

To keep the external monitor from going blank when you close the laptop's lid, got to Preferences -> Power Management and set "When laptop lid is closed" to "Do nothing".

---


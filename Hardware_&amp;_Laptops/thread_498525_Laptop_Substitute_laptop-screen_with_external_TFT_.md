---
title: "Laptop: Substitute laptop-screen with external TFT (when connected)"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by locki85 on 2007-07-11
Hello!

I own a laptop with a native resolution of 1400x1050. Just recently, I bought an additional 19" TFT screen (maximal supported resolution of 1280x1024). I want to substitute the built-in laptop screen with the new TFT, when it is connected (via VGA).

So what I want, is this:
a) Start system with TFT connected -> Resolution 1280x1024 -> TFT on, laptop screen of.
b) Start system without TFT connected (mobile use) -> Resolution 1400x1050 -> Laptop screen on

What I got now, is this:
Start system with TFT connected -> Resolution 1400x1050 -> TFT off (resolution not supported), laptop screen on.

When I manually change the resolution to 1280x1024, the TFT turns on, but the laptop screen does not turn off. So I need to go to the ATI Cataclyst Control Center (I have ATI driver 8.38.6 installed), and turn the laptop screen off. Works, but the problem is, I need to do this on EVERY system start.

Somebody can help me with this annoyance?

---

### Post by qamelian on 2007-07-11
You probably need to edit the mode lines for the second screen in /etc/X11/xorg.conf. You can remove the resolutions that you don't want for the second screen.

---

### Post by locki85 on 2007-07-11
> **qamelian said:**
> You probably need to edit the mode lines for the second screen in /etc/X11/xorg.conf. You can remove the resolutions that you don't want for the second screen.

Been there, done that. No change. I'll paste the important parts of my xorg.conf at the end of the post...
Messed with it a lot, so its looks probably a bit screwed up (and hopefully full of errors, that you can help me to correct, so it will work ;))


```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0       "Laptop" 0 0
	Screen 1       "TFT" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	#Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "v4l"
	Load  "vbe"
EndSection

### Laptop Display ###

Section "Monitor"
	Identifier   "Samsung LCD"
	HorizSync    30.0 - 75.0
	VertRefresh  50.0 - 85.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X600"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Screen"
	Identifier "Laptop"
	Device     "ATI Mobility Radeon X600"
	Monitor    "Samsung LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1280x1024"
	EndSubSection
EndSection

### TFT ###
Section "Monitor"
    Identifier     "Belinea TFT"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X600"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "TFT"
	Device     "ATI Mobility Radeon X600"
	Monitor    "Belinea TFT"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

```

---

### Post by qamelian on 2007-07-11
I think the problem is that both device sections for the graphics card are using the same identifier. I believe you need to differentiate between the two. For example, change one to Primary and the other to Secondary, instead of both having the model of your graphics card. The link below might help you:
[http://ubuntuforums.org/showthread.php?t=31686&highlight=dual+head](http://ubuntuforums.org/showthread.php?t=31686&highlight=dual+head)

---

### Post by KRossKoWolf on 2007-07-11
Just a thought, but from what he says it sounds like another solution might be to remove the resolution of the TFT from the section about the Laptop LCD, so it's like this,

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0       "Laptop" 0 0
	Screen 1       "TFT" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	#Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "v4l"
	Load  "vbe"
EndSection

### Laptop Display ###

Section "Monitor"
	Identifier   "Samsung LCD"
	HorizSync    30.0 - 75.0
	VertRefresh  50.0 - 85.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X600"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Screen"
	Identifier "Laptop"
	Device     "ATI Mobility Radeon X600"
	Monitor    "Samsung LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

### TFT ###
Section "Monitor"
    Identifier     "Belinea TFT"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X600"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "TFT"
	Device     "ATI Mobility Radeon X600"
	Monitor    "Belinea TFT"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection
```

---

### Post by locki85 on 2007-07-12
qamelian: I see what you mean, but that wont work for me, because I have only one graphics-card. So I can use only one identifier, and also the howto from your link does not work for me...

KRossKoWolf: Thanks for your answer, I already tried it but it did not work. Problem is, both monitors can only use the same resolution, so I need to provide the 1280 for both.



What I managed so far: I changed the resolution of the laptop from 1400 to 1280 as *default*, from the Ubuntu menu. Same changes in the Cataclyst control center would not have been saved. So the TFT turns on after login now, because Ubuntu's default resolution is supported now.

But I still need to find a way to turn the laptop screen of by default (if I work stationary), or let it use 1400 by default, if the TFT is not connected (mobile use).

Is there maybe any way, that my screens use two *different* resolutions?

---

### Post by KRossKoWolf on 2007-07-12
You might want to take a little look at this, [http://ubuntuforums.org/showthread.php?t=119112]("http://ubuntuforums.org/showthread.php?t=119112")  , see if that can help any.

---

### Post by qamelian on 2007-07-12
> **locki85 said:**
> qamelian: I see what you mean, but that wont work for me, because I have only one graphics-card. So I can use only one identifier, and also the howto from your link does not work for me...


It works for me and I only have one graphics card: the ATI Mobility Radeon 9000 IGP in my laptop. I have the xorg.conf in my laptop setup as I've described and have no problem using an external monitor with it.

---

### Post by qamelian on 2007-07-12
Not sure if this will help sort out your problem, but there is a gui tool called displayconfig-gtk that is available in the Universe repository for both Feisty and Gutsy. I've used it on my other test box with some success.

---


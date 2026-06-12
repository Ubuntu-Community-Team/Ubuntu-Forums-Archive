---
title: "nvidia driver: Direct Rendering seems to have stopped working!"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by TehDooMCat on 2008-03-23
**EDIT: I discovered the problem. For no apparent reason when Compiz loads up now it says 'Checking for nVidia: not present.' even though I'm using the 'nvidia' (not 'nv') driver and all! Not sure why it makes Xorg crash though, or how to get it to use nvidia's rendering again :confused:**

For no apparent reason today, when I booted my comp up, gdm started up and logged me in as per usual, but as it was logging in my computer became very unresponsive (mouse very very **very** choppy), and then the xserver restarted. It'd do this every time I logged in so I booted into Failsafe GNOME which ran perfectly. I assumed it was a problem with GL or Compiz or something, although I couldn't find the logs for Compiz (if it does actually log anything)

Being the idiot that I am, I decided to install Xgl. It actually fixed compiz, to an extent. However, it was running slower than before and in the process I'd mucked up my xorg.conf. Running glxgears would slow compiz down far too much, but it still said it was doing over 10,000FPS. When I looked at glxinfo it told me there was no direct rendering, so I reverted to the old xorg.conf. However, direct rendering still didn't work, and running glxgears still slowed stuff down far too much. I edited these sections of xorg.conf to try and get DRI working:

Section "Module"
	Load		"glx"
	Load		"v4l"
	Load		"dri"
	Load		"GLcore"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"RenderAccel"	"true"
	Option		"AllowGLXWithComposite"	"true
	Screen	0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "DRI"
	Mode	0666
EndSection

Also, Section "Files" didn't have any entries in it, and I'm sure it had some beforehand.

With RenderAccel enabled and dri loaded, I still don't get direct rendering according to glxinfo. :confused:

Can someone show me how to get DRI working again? I want my comp back to the way it was before this morning - I could run two games and a fullscreen film with compiz running smooth enough before, now a program that renders gears slows it down :(

And how can I disable Xgl? I don't think I need it; it just seems to put more strain on the CPU when Compiz does effects.

---


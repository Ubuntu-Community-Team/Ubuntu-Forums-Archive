---
title: "Circular Scrolling on Intrepid (8.10)"
date: 2008-11-12
forum: General Help
---

### Post by chmac on 2008-11-12
G'day,

I'm trying to enable circular scrolling on Intrepid but my xorg.conf is empty by default.

Can I enable circular scrolling without filling out the whole xorg.conf?

Any suggestions?

---

### Post by Jacob111 on 2008-11-19
Ya I'm wondering about this too.  This is the first version of Ubuntu where your Xorg doesn't have control over input devices, like the mouse.  The update from hardy commented out all those lines, but uncommenting them and changing the code makes no difference.  If someone could point us to where we go to edit device configurations that would be nice.

---

### Post by chmac on 2008-11-20
The xorg.conf does still work in 8.10, but if it's empty, X will fill in sensible defaults as best it can, and should "just work" in most use cases. To enable circular scrolling, I have recreated the essential sections of my xorg.conf such that it now looks like this:
```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	# Circular scrolling options
	Option     	"CircularScrolling" "1"
	Option      	"CircScrollTrigger" "3"
	Option      	"Emulate3Buttons" "yes"
	Option      	"SHMConfig" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Configured Screen Device"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Circular scrolling is working for me with this setup. You might have to play with the Synaptics options above the "#Circular Scrolling Options" line as those may be specific to my setup. But otherwise, if you copy / paste this into your xorg.conf I'd guess it will work.

Remember, if it goes wrong, you can CTRL-ALT-F1 and then delete xorg.conf altogether, that should give you a working desktop again. But if everything goes wrong and your world ends, please don't hold me responsible. Use at your own discretion! :)

---

### Post by Altay_H on 2009-01-02
In case anyone reading this is having trouble getting circular scrolling to work with the way mentioned above, there's an alternative way that worked for me at this thread: [http://guide.ubuntuforums.org/showthread.php?t=1026599](http://guide.ubuntuforums.org/showthread.php?t=1026599)


Basically, first you install gsynaptics:
```
sudo apt-get install gsynaptics
```

Then you follow this short guide:
[http://ubuntuforums.org/showpost.php?p=6077309&postcount=121](http://ubuntuforums.org/showpost.php?p=6077309&postcount=121)

Now you can enable circular scrolling by going to:
System > Preferences > Touchpad > Scrolling > Enable Circular Scrolling


I hope this helps someone.

---

### Post by chmac on 2009-01-02
Altay_H, that's an awesome tip, gsynaptics seems like a much easier option.

---


---
title: "Sony Vaio Trackpad Speed"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by davidingram on 2007-12-08
Hi, I have ubuntu 7.10 Gutsy on my Sony Vaio VGN-T150 Laptop.  Everything works fine but the trackpad is very slow.  I have tried changing the mouse speed up in the PREFERENCES / MOUSE / MOTION, but that doesnt change the trackpad.  There are no settings for speed on the trackpad tab.  Any ideas.  Its very frustrating to have to do multiple strokes on the touchpad just to get across the screen.  Thanks for any help.  David.

---

### Post by ubun2dragon on 2007-12-08
Hi,

I had the same problem on my notebook, although it's not a Vaio.  I am presuming it uses the synaptics touchpad driver, hope this helps.  There are several ways to fix the issue.  I'll explain how I fixed the issue manually, and then the other ways (which didn't work for me).

In Terminal type sudo gedit /etc/X11/xorg.conf

When xorg.conf comes up in gedit, look for the following section.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"

I had to add the following items to the section in order to speed up my synaptics touchpad

	Option		"SHMConfig"		"true"
	Option		"MinSpeed"		"0.5"
	Option		"MaxSpeed"		"0.9"
	Option		"AccelFactor"		"0.1"

You can also try downloading gsynaptics or qsynaptics and try to configure the touchpad speed using them.  Just do a search on them and you'll find some good information on how to install/configure.  You'll have to do things like add the SHMGConfig line to your xorg.conf file, and restart X after you have installed the package.  Even though I followed the instructions and gsynaptic and qsynaptic seemed to run fine, neither of them affected the touchpad speed and that is why I ended up adding the above settings manually.

---

### Post by davidingram on 2007-12-10
OMG, that is BRILLIANT!  Thanks Ubunt2Dragon.:)

I am no techie, and editing anything like that scares me, but, it worked brilliantly.

BIG THANKS.

D (a very satisfied new Ubuntu user).

*PS: Just on the offchance that you know this too... my volume control buttons (and mute) on the front of the viao don't function in Ubuntu.  So i have to use the volume control in the UI (which works fine, but is less convenient than the hardware buttons).  Do you also happen to know a fix for this?*

---

### Post by davidingram on 2007-12-10
Uho, Now I have another problem.  I spoke too soon.

This could be related or totally unrelated to the fix above, but my sound no longer works at all.  The volume is up, its not muted, but still nothing.

Any ideas most welcome.
Thanks. D

---

### Post by davidingram on 2007-12-10
Jeez, I am such a noob.  I just fixed it.  I went into Applications / SOund and Video / Gnome ALSA Mixer and tried ticking and unticking a few boxes.  The PCM mute box was ticked so i unticked it and now I have sound.  Hooray.  I have no idea how that got muted in teh first place, but hohum, its all good now.

Any help on that hardware volume buttons would be appreciated.  They are still non-functional.

D

---


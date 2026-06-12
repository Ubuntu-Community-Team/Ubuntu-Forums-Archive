---
title: "enabling effects messes up scrolling"
date: 2008-08-29
forum: General Help
---

### Post by thousandpimps on 2008-08-29
so i just installed my video card nvidia 8200m and it works good i think...but i just realized that when i scroll on a web page the text gets scrambled up ...so i went and selected no effects and then everything is fine...can anyone tell me what i can do to solve this problem...and i also want to have some effects..
thanks a lot

---

### Post by el_escorpion on 2008-09-16
Hi all, I got the same problem. I spend an hour trying to get the nVidia drivers to work. When I finally got it to work it scrambles text when i scroll, not to mention the scrolling part of the touch pad stopped working...

Any help would be appreciated as I have no clue where the problem might be.

---

### Post by jjones22 on 2008-09-17
I have the same problem with my Nvidia 8200 and have been searching for a solution with no luck.  The Nvidia 8200 chipset has been a nightmare with ubunutu; it wouldnt detect the hard drive, the sound card does not work (I had to install a new sound card), and now the video driver messes up scrooling when effects are enabled.  I would not recommend this chipset for anyone buying a new system.

---

### Post by mb_webguy on 2008-09-17
> **el_escorpion said:**
> Hi all, I got the same problem. I spend an hour trying to get the nVidia drivers to work. When I finally got it to work it scrambles text when i scroll, not to mention the scrolling part of the touch pad stopped working...

Any help would be appreciated as I have no clue where the problem might be.

If you have a Synaptics touchpad, make sure your /etc/X11/xorg.conf file entry looks something like the following:```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

```

If you see anything about VerticalEdgeScroll being set to 0 or False, remove that line or set it to True.

As for the other problems...  sorry, guys.  I have the nVidia 8400M chipset, and it works beautifully.

---

### Post by bjbeeson on 2008-09-18
I was having the same problem.  Here is what I did to solve it.  First, before you try this I want to let you know that I don't know what I am doing.

I am using Avant Windows Naviagator and effects turned on normal.

I installed CCSM.  Under the behavior tab of the widget icon I added the following - name=avant-window-navigator.

That solved the problem.

I hope it works for you.

---

### Post by bopomofo on 2008-09-23
> **bjbeeson said:**
> I was having the same problem.  Here is what I did to solve it.  First, before you try this I want to let you know that I don't know what I am doing.

I am using Avant Windows Naviagator and effects turned on normal.

I installed CCSM.  Under the behavior tab of the widget icon I added the following - name=avant-window-navigator.

That solved the problem.

I hope it works for you.

I'm confused. What problem does this solve? The only effect of this is to put AWN on the Widgets layer, and I can't see a) why this is desirable or b) how this is related to the scrolling problem (which I am also experiencing on an NVIDIA chipset.

---


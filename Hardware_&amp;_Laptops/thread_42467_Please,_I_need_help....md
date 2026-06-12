---
title: "Please, I need help..."
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by hasenkamp on 2005-06-17
I don't know what is going on, my system is really slow.

I already have tried hdparm settings, the X is working fine, but I don't know why the computer is so slow.

My system:
P3 800
i810 (shared video card)
192Mb
etc...

I tried free and I got 
           [INDENT]  total       used     **  free **    shared    buffers     cached[/INDENT]
Mem:        190760     186452      ** 4308 **         0        932      34984
-/+ buffers/cache:     150536      40224
Swap:       433744      53636     380108


It seems that my memory is full...

Please someone could help me, I don't know what to do...I'm have no experience on linux.

Thanks

---

### Post by desdinova on 2005-06-17
Your machine is a little on the low side for memory - perhaps try installing and running XFCE rather then Gnome?

---

### Post by gil-galad on 2005-06-17
Yeah.  Gnome needs 256mb to run smoothly.  Plus your video card is probably eating ram.

---

### Post by hasenkamp on 2005-06-17
I'm using the last kde... I completely dislike gnome

I already have tried xfce... its nice... but it continue slow... I really don't know what it could be.

Thanks

---

### Post by desdinova on 2005-06-17
KDE also needs 256 + - either add some extra memory, or try something like OpenBox/Fluxbox or ICEWM - 192mb is a bit low for a highend gui

---

### Post by hasenkamp on 2005-06-17
Yeah, I know that 256mb is needed...

What I was tring to say is that I already have tried XFCE, Fluxbox and windowmaker, but the same problem apear. Something is going wrong, and I don't know how to discover what it could be.

gil-galad have suggested that could be the video card eating ram... but how to solve this. Maybe the driver I have been using... i810.  How can I change to vesa or other one directly on xorg.conf without execute xorgconfig?

Thanks for the help

---

### Post by intangible on 2005-06-18
Check the settings in your BIOS, make sure you aren't giving the onboard video too much RAM, 2MB should be fine, but I've seen some BIOSes give 10MB to the onboard video!! UGH!

---

### Post by wvslkr on 2005-06-18
First of all, to change to vesa, open Xorg,conf in your text editor of choice (use sudo)and change driver to vesa.

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PP/PRO (TMDS Xpert 128)"
	Driver		"ati"
	BusID		"PCI:0:18:0"
EndSection

In this case "ati" to "vesa".

In the matter of how slow your system is. that is partly subjective.  I am running on a p233mmx with 192meg ram and swap from what you state is about what  I use.  I run KDE, Gnome, and XFCE, depending on my mood and can see no major differences except XFCE loads a little faster.  Apps take a little bit to load but perform well after starting.  The  caveat is if you plan running more than a couple or three things at once you will go to swap, which is slow.  The only way to cure it is add more ram.  Linux will use as much ram as you feed it:  thus caching processes in ram unless needed to run something else.

Being said. I find my system usable, but not fast, not expected on the equipment.  If however you are extremely slow, check >System>System Monitor  and see if something is using an obscene amount of memory or cpu time.

In short I run I much slower cpu with same ram and it is fine for me.  Your threshold may be different.  If you are not being unrealistic on performance extpectations, look for a rogue application.

Hope you sort things out.  GL. :)

---

### Post by hasenkamp on 2005-06-18
Thanks for the help guys...

I will not be able to change the settings this weekend but as soon as monday comes I will try to change "i810" to "vesa".

Some really strange thing I have experinced was that even with "nothing" running, only the basic process, if I try to open a new application its like to have a baby... takes 9 months... :neutral:

I already have checked the amount of ram shared with the video card. its set to 1Mb (max).

I also have tryed a P2 400Mhz, just to compare, and the conclusion was that Its more confortable to use the P2 than my P3  :???:.

Thanks again.

---


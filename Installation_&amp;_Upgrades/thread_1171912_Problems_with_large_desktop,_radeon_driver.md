---
title: "Problems with large desktop, radeon driver"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by todd534 on 2009-05-27
I have a Thinkpad T60 with an ATI Radeon Mobility x1300. In Intrepid, I used fglrx and had things configured such that I could attach an external monitor at 1600x1200, using a virtual line in xorg.conf of 3000x1200. 

I upgraded to Jaunty, switched from fglrx to radeon, and now this doesn't work. I can attach the external monitor at sizes up to 1400x1050 (coincidentally? the resolution of the LCD), and it works great. You can see what the desktop looks like here: [http://www.flickr.com/photos/todd534/3571291501/](http://www.flickr.com/photos/todd534/3571291501/)

At higher resolutions, the display works but starts to act really weird. The background is black, weird lines run upward from the 'gnome-do' dock thing, and moving windows around results in trails of where the windows used to be. A screenshot of only mild weirdness is here: [http://www.flickr.com/photos/todd534/3572097150/](http://www.flickr.com/photos/todd534/3572097150/) ; sometimes it looks worse. 

xorg.conf as follows, but it's pretty much bare, except for the virtual screen line: 

```
Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3000 1200
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver	"radeon"
	BusID       "PCI:1:0:0"
EndSection
```

I tried turning off compiz, that didn't seem to help, but I didn't mess with it for too long because I like transparency and it used to work with fglrx. I've been googling about this for a week or two, getting no where. Any ideas greatly appreciated. I'd like to at least be able to isolate if this is a bug in some project, so I can submit a bug report.

---

### Post by Sheffy on 2009-05-27
its because a LOT of people have had issues with ATI graphics cards. you have to get NVidea GeFORCE. theyre not that expensive. FRYS is overpriced though

---

### Post by todd534 on 2009-05-28
Well, first, it's a laptop with integrated graphics, so "your video card is teh lame" is a non-starter. Second, I've already had what I want with fglrx, so it's not like an inherent limitation of the device.

---

### Post by The Foz on 2009-05-28
I am also having problems after installing 9.04, although nothing as drastic.

I installed 9.04 (the 64 bit version) in another partition, so I can still run the 32 bit 8.10 OS (I have lots of stuff still to migrate).

I now have rendering performance issues, which seems to be either Xorg itself, or the Radeon driver. In 8.10 the driver ran multi-threaded; in 9.04 it seems that it doesn't. Since I have the pathetic ES1000 graphics chip, virtually all the rendering work is done in software, so this is a big issue.

I can no longer play a video (in VLC) full-screen without it running slow. If I open the system monitor, that alone takes about 100% of one CPU when the window is at full size (the load reduces as I make the window smaller).

I have a quad Xeon, running at 1.86 GHz. That is a lot of power, but Xorg or the driver is no longer able to fully harness that power.

I do eventually plan to get a real graphics card, but that will have to wait a few months. I don't think it unreasonable to expect the graphics to work as well under Jaunty as under Hardy. I had hoped that graphics performance would improve a bit, due to the change from 32 bit to 64 bit.

---

### Post by ssam on 2009-05-28
have you tried clearing the xorg.conf (use the xfix recovery option at boot time.) then use the system->preference->screen-resolution (or display or whatever it is called). it should set up a simple xorg.conf.

if you still have trouble then you could try the slightly newer radeon drivers.

[http://ubuntuforums.org/showthread.php?t=1138689](http://ubuntuforums.org/showthread.php?t=1138689)

i say stick with ati. they have been releasing lots of specs for their graphics cards. the driver development is going pretty fast currently, so things are a bit bumpy. nvidia users will be stuck with closed source drivers for the foreseeable future.

---

### Post by The Foz on 2009-05-28
Hi ssam,

Would be nice to know who your remarks were addressed to.

---

### Post by ssam on 2009-05-28
that was aimed at todd.

i have never heard of the ES1000 chip, but the PPA may help with that too.

---

### Post by todd534 on 2009-05-28
Eh, yeah. I mean, I've tried clearing xorg with dpkg-reconfigure. It tends to put in 'ati' instead of 'radeon,' and then I get a worse behavior (basically with compiz enabled I get a blank white screen when I log in). I get the same behavior if I put in 'radeonhd,' so I assume 'ati' is trying to smartly choose between the two and picking the wrong one.

It also doesn't put in the 'virtual' line, and if I recall correctly I couldn't get the large desktop I want without it.

But I'll try the newer radeon driver. That sounds promising. Thanks.

---

### Post by todd534 on 2009-05-28
Yeah, no help with the PPA driver so far. Oh well.

---

### Post by todd534 on 2009-05-28
I just discovered that I can fix this problem with 
```
killall nautilus
```

Further, if I activate nautilus again, the weirdness returns. That's pretty exciting. I also get this in the terminal where I run it: 
> ** (nautilus:30610): WARNING **: Unable to add monitor: Not supported

So I guess it's a nautilus issue. Which is great news, since I use the graphical file manager pretty sparingly and don't keep much on my desktop.

---

